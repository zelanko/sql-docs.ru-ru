---
title: "Шаг 5: Обучение и сохранить модель Python, с помощью T-SQL | Документы Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: python-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: bcad930d7d2a759e66adf1309eba6af144010c82
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="step-5-train-and-save-a-python-model-using-t-sql"></a>Шаг 5: Обучение и сохранить модель Python, с помощью T-SQL

В этой статье является частью учебника [analytics Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы узнаете, как для обучения модели машинного обучения с помощью пакетов Python **scikit-Узнайте** и **revoscalepy**. Эти библиотеки Python службами SQL Server Machine Learning уже установлены.

Загрузки модулей и вызов функции, необходимые для создания и обучения модели с помощью хранимой процедуры SQL Server. В модели необходимо данных компонентов, разработан на предыдущих занятиях. Наконец, сохраните обученной модели для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.

> [!IMPORTANT]
> Будут внесены некоторые изменения в **revoscalepy** пакет, который требуется небольшие изменения в коде в этом учебнике. В разделе [changelist](sqldev-py6-operationalize-the-model.md#changes) в конце этого учебника. 
> 
> Если установлены службы Python, с помощью предварительной версии SLq Server 2017 г., рекомендуется обновить до последней версии. 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Разбить образцы данных на обучающий и проверочный наборы

1. Можно использовать хранимую процедуру **TrainTestSplit** для разделения данных в nyctaxi\_образец таблицы на две части: nyctaxi\_пример\_обучения и nyctaxi\_пример\_тестирования. 

    Эта хранимая процедура должна уже создан, но можно запустить следующий код, чтобы создать его:

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

2. Чтобы разделить данные с помощью пользовательской разворачивающейся, запустите хранимую процедуру и введите целое число, представляющее процент данных, размещаемых в обучающий набор. Например следующая инструкция будет выделить 60% данных в обучающий набор.

    ```SQL
    EXEC TrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Построить модель логистической регрессии

После подготовки данных его можно использовать для обучения модели. Это можно сделать, вызвав хранимую процедуру, которая выполняет код Python, используя в качестве входных данных в таблице обучающих данных. В этом учебнике создайте две модели, обе модели двоичной классификации:

+ Хранимая процедура **TrainTipPredictionModelRxPy** создается модель прогнозирования подсказки с помощью **revoscalepy** пакета.
+ Хранимая процедура **TrainTipPredictionModelSciKitPy** создается модель прогнозирования подсказки с помощью **scikit-узнать** пакета.

Каждая хранимая процедура использует входные данные предоставляют для создания и обучения модели логистической регрессии. Весь код Python упаковывается в системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Для упрощения повторного обучения модели на новые данные программу-оболочку вызова sp_execute_exernal_script в другой хранимой процедуры и передайте новый обучающих данных, как параметр. Этот раздел поможет выполнить данный процесс.

### <a name="traintippredictionmodelscikitpy"></a>TrainTipPredictionModelSciKitPy

1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новый **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelSciKitPy_.  Хранимая процедура содержит определение входных данных, вам требуется для предоставления входного запроса.

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

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Эта хранимая процедура использует новый **revoscalepy** пакет, который представляет новый пакет для Python. Он содержит объекты, преобразование и алгоритмы, аналогичные указанным для языка R **RevoScaleR** пакета. 

С помощью **revoscalepy**, можно создать контекстах удаленных вычислений, перемещения данных между вычислений контекстов, преобразование данных и обучение прогнозных моделей с помощью популярные алгоритмы, такие как логистическая и линейной регрессии дерева принятия решений и Дополнительные. Дополнительные сведения см. в разделе [возможности revoscalepy?](../python/what-is-revoscalepy.md)

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новый **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelRxPy_.  Так как хранимая процедура уже содержит определение входных данных, не требуется для предоставления входного запроса.

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
    from revoscalepy.functions.RxLogit import rx_logit
    
    ## Create a logistic regression model using rx_logit function from revoscalepy package
    logitObj = rx_logit("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
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

    - Запрос SELECT применяет скалярной пользовательской функции _fnCalculateDistance_ для расчета прямой расстояния между расположениями отправки и истощение. Результаты запроса сохраняются в Python входной переменной по умолчанию, `InputDataset`.
    - Двоичный переменной _чаевых оставил зависимости_ используется в качестве *метка* или столбец результата и модели является подогнать эти столбцы компонентов: _passenger_count_, _trip_ расстояние_, _trip_time_in_secs_, и _direct_distance_.
    - Сериализуется и сохраняется в переменной Python обученной модели `logitObj`. Добавив ключевое слово T-SQL выходные данные, можно добавить переменную как выходные данные хранимой процедуры. В следующем шаге, эта переменная используется для вставки в таблицу базы данных двоичного кода модели _nyc_taxi_models_. Этот механизм позволяет легко хранить и повторно использовать модели.

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

[Шаг 6: Ввода в эксплуатацию модели Python, с помощью SQL Server](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Предыдущий шаг

[Шаг 4. Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
