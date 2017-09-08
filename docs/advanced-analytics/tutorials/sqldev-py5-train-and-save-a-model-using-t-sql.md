---
title: "Шаг 5. Обучение и сохранение модели с помощью T-SQL | Документация Майкрософт"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80a47819dfbb2e96162a49730e0dcf0b1b340f07
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="step-5-train-and-save-a-model-using-t-sql"></a>Шаг 5: Обучение и сохранить модель с помощью T-SQL

На этом шаге вы узнаете, как для обучения модели машинного обучения с помощью пакетов Python **scikit-Узнайте** и **revoscalepy**. Эти библиотеки Python уже установлены со службами SQL Server машины обучения для загрузки модулей и вызывать необходимые функции из хранимой процедуры. Вы обучите модель с помощью только что созданных характеристик данных, а затем сохраните обученную модель в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Разбить образцы данных на обучающий и проверочный наборы

1. Выполните следующие команды T-SQL для создания хранимой процедуры, которая распределяет данные в nyctaxi\_образец таблицы на две части: nyctaxi\_пример\_обучения и nyctaxi\_пример\_тестирования.

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. Запустите хранимую процедуру и введите целое число, представляющее процент данных, размещаемых в обучающий набор. Например следующая инструкция будет выделить 60% данных в обучающий набор. Обучающие и проверочные данные хранятся в двух отдельных таблицах.

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model-using-scikit-learn"></a>Создать модель логистической регрессии, scikit-Дополнительные сведения

В этом разделе создайте хранимую процедуру, которая может использоваться для обучения модели с помощью только что подготовленном обучающих данных. Эта хранимая процедура определяет входные данные и использует **scikit-узнать** функции для обучения модели логистической регрессии. Вызов среды выполнения Python, который устанавливается вместе с SQL Server с помощью системной хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Для упрощения повторного обучения модели можно заключать вызов sp_execute_exernal_script в другой хранимой процедуры и передайте новый обучающих данных, как параметр. Этот раздел поможет выполнить данный процесс.

1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новый **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelSciKitPy_.  Обратите внимание, что хранимая процедура содержит определение входных данных, вам требуется для предоставления входного запроса.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelSciKitPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelSciKitPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
      EXEC sp_execute_external_script
      @language = N'Python',
      @script = N'
      import numpy
      import pickle
      import pandas
      from sklearn.linear_model import LogisticRegression
      
      ##Create SciKit-Learn logistic regression model
      X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
      y = numpy.ravel(InputDataSet[["tipped"]])
      
      SKLalgo = LogisticRegression()
      logitObj = SKLalgo.fit(X, y)
      
      ##Serialize model
      trained_model = pickle.dumps(logitObj)
      ',
      @input_data_1 = N'
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_training
      ',
      @input_data_1_name = N'InputDataSet',
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT;
      ;
    END;
    GO
    ```

2. Выполните следующие инструкции SQL для вставки обученной модели в таблице nyc\_taxi_models.

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelSciKitPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Обработка данных и соответствует модели может занять несколько минут. Сообщения, которые может быть выведен Python **stdout** потока отображаются в **сообщений** окно [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Например:

    *Сообщения STDOUT из внешнего скрипта:*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. Откройте таблицу *nyc\_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *linear_model* *0x800363736B6C6561726E2E6C696E6561...*

## <a name="build-a-logistic-model-using-the-revoscalepy-package"></a>Построение с помощью модели логистической _revoscalepy_ пакета

Теперь создайте другой хранимой процедуры, в котором используется новый **revoscalepy** пакета для обучения модели логистической регрессии. **Revoscalepy** пакета Python содержит объекты, преобразования и алгоритмы, аналогичные указанным для языка R **RevoScaleR** пакета. С этой библиотеки можно создать контекст вычислений, перемещение данных между контексты вычислений, преобразования данных и обучения моделей прогнозирования с помощью популярные алгоритмы, такие как логистическая и линейной регрессии, деревья принятия решений и многое другое. Дополнительные сведения см. в разделе [возможности revoscalepy?](../python/what-is-revoscalepy.md)

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новый **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelRxPy_.  Эта модель также использует только подготовленном обучающих данных. Так как хранимая процедура уже содержит определение входных данных, не требуется для предоставления входного запроса.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

    Эта хранимая процедура выполняет следующие действия в процессе обучения модели.

    - Обучение модели логистической регрессии с помощью пакета revoscalepy на nyctaxi\_пример\_обучающих данных.
    - Запрос SELECT использует пользовательскую скалярную функцию _fnCalculateDistance_ для вычисления прямого расстояния между местами посадки и высадки. Результаты запроса сохраняются в Python входной переменной по умолчанию, `InputDataset`.
    - Сценарий Python вызывает revoscalepy LogisticRegression функции, которая входит в состав [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], чтобы создать модель логистической регрессии.
    - Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик:  _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
    - Обученную модель, содержащегося в переменной Python `logitObj`, сериализованы и поместить в качестве выходного параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Что выходные данные вставлены в таблицу базы данных _nyc_taxi_models_, вместе с его именем в новую строку, можно получить и использовать его для будущих прогнозов.

2. Выполнение хранимой процедуры, как показано ниже, чтобы вставить обученной **revoscalepy** модели в таблице _nyc\_такси\_моделей.

    ```SQL
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Обработка данных и соответствует модели может занять некоторое время. Сообщения, которые может быть выведен Python **stdout** потока отображаются в **сообщений** окно [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Например:

    *Сообщения STDOUT из внешнего скрипта:*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. Откройте таблицу *nyc_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *rx_model* *0x8003637265766F7363616c...*

На следующем шаге обученных моделей используется для создания прогнозов.

## <a name="next-step"></a>Следующий шаг

[Шаг 6: Ввода в эксплуатацию модели](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Предыдущий шаг

[Шаг 4: Создание компонентов данных, с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

