---
title: 'Обучение и сохранение модели Python с помощью T-SQL: машинного обучения SQL Server'
description: Учебник по Python, показывающий, как обучение и сохранение модели с помощью Transact-SQL на сервере SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2e0505cf847a091a5650b392aab56f486cee16aa
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511251"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Обучение и сохранение модели Python с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит учебник по, [Python в базе данных аналитики для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы узнаете, как обучить модель машинного обучения, с помощью пакетов Python **scikit-Узнайте** и **revoscalepy**. Эти библиотеки Python уже установлены с помощью служб машинного обучения SQL Server.

Загрузки модулей и вызывать необходимые функции для создания и обучения модели с помощью хранимой процедуры SQL Server. В модели необходимо возможности данных, которые разработаны в ходе предыдущих занятий. Наконец, сохраните обученную модель для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Разбить демонстрационные данные на обучающий и проверочный наборы

1. Создайте хранимую процедуру с именем **PyTrainTestSplit** разделения данных в таблицу nyctaxi_sample на две части: nyctaxi_sample_training и nyctaxi_sample_testing. 

    Эта хранимая процедура должна быть создана для вас, но можно запустить следующий код, чтобы создать его:

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainTestSplit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. Чтобы разделить данные с помощью пользовательского разбиения, выполните хранимую процедуру и введите целое число, представляющее процент данных, размещаемых в обучающий набор. Например следующая инструкция выделит 60% данных в обучающий набор.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Создать модель логистической регрессии

После подготовки данных, его можно использовать для обучения модели. Это делается путем вызова хранимой процедуры, которая запускается код Python, используя в качестве входных данных в таблице обучающих данных. Для этого руководства создайте две модели, обе модели двоичной классификации:

+ Хранимая процедура **PyTrainScikit** создает модель прогнозирования подсказки с помощью **scikit-Узнайте** пакета.
+ Хранимая процедура **TrainTipPredictionModelRxPy** создает модель прогнозирования подсказки с помощью **revoscalepy** пакета.

Каждая хранимая процедура использует входные данные предоставляют для создания и обучения модели логистической регрессии. Весь код Python упаковывается в системную хранимую процедуру, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Чтобы упростить повторное Обучение модели на основе новых данных, поместите вызов процедуры sp_execute_exernal_script в другой хранимой процедуры и передать в качестве параметра новый обучающих данных. В этом разделе поможет выполнить этот процесс.

### <a name="pytrainscikit"></a>PyTrainScikit

1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новую **запроса** окна и выполните следующую инструкцию, чтобы создать хранимую процедуру **PyTrainScikit**.  Хранимая процедура содержит определение входных данных, поэтому входной запрос указывать не нужно.

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainScikit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainScikit] (@trained_model varbinary(max) OUTPUT)
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

2. Выполните следующие инструкции SQL для вставки обученную модель в таблице Нью-Йорка\_taxi_models.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Обработка данных и компоновка модели может занять несколько минут. Сообщения, которые должны передаваться в Python **stdout** потока отображаются в **сообщений** окно [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Пример:

    *Сообщения STDOUT из внешнего скрипта:*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. Откройте таблицу *Нью-Йорка\_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561...*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Эта хранимая процедура использует новый **revoscalepy** пакет, который представляет новый пакет для Python. Он содержит объекты, преобразования и алгоритмы, аналогичные указанным для языка R **RevoScaleR** пакета. 

С помощью **revoscalepy**, можно создать удаленные контексты вычисления, перенос данных между вычислительных контекстов, преобразовывать данные и прогнозных моделей обучения, используя популярные алгоритмы, такие как логистическая и Линейная регрессия, деревья принятия решений, и Дополнительные. Дополнительные сведения см. в разделе [revoscalepy модуля в SQL Server](../python/ref-py-revoscalepy.md) и [Справочник по функциям revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новую **запроса** окна и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelRxPy_.  Так как хранимая процедура уже включает в себя определение входных данных, входной запрос указывать не нужно.

    ```sql
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

    Эта хранимая процедура выполняет следующие действия в процессе обучения модели:

    - Запрос SELECT применяет пользовательскую скалярную функцию _fnCalculateDistance_ для вычисления прямого расстояния между местами посадки и высадки. Результаты запроса сохраняются в входной переменной Python по умолчанию, `InputDataset`.
    - Двоичная переменная _tipped_ используется в качестве *метка* или столбец результата и модель компонуется с использованием следующих столбцов характеристик: _passenger_count_, _trip_ расстояние_, _trip_time_in_secs_, и _direct_distance_.
    - Обученную модель сериализуется и сохраняется в переменной Python `logitObj`. Добавляя ключевое слово T-SQL выходные данные, можно добавить переменную как выходные данные хранимой процедуры. На следующем шаге эта переменная используется для вставки двоичный код модели в таблицу базы данных _nyc_taxi_models_. Этот механизм позволяет легко хранить и повторно использовать модели.

2. Выполните хранимую процедуру таким образом, чтобы вставить обученной **revoscalepy** модель в таблицу *nyc_taxi_models*.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Обработка данных и компоновка модели может занять некоторое время. Сообщения, которые должны передаваться в Python **stdout** потока отображаются в **сообщений** окно [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Пример:

    *Сообщения STDOUT из внешнего скрипта:*
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site packages\revoscalepy*

3. Откройте таблицу *nyc_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *revoscalepy_model* *0x8003637265766F7363616c....*

В следующем шаге обученных моделей используется для создания прогнозов.

## <a name="next-step"></a>Следующий шаг

[Запустите прогнозы с помощью Python, внедренных в хранимую процедуру](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
