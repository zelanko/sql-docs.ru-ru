---
title: Python и T-SQL. Обучение модели
description: Учебник по Python, демонстрирующий обучение и сохранение модели с помощью Transact-SQL на сервере SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b8bec553502b2e5c8d69436e539437be9a5989aa
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73724875"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Обучение и сохранение модели Python с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья является частью руководства [Анализ с помощью Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы узнаете, как обучить модель машинного обучения с помощью пакетов Python **scikit-learn** и **revoscalepy**. Эти библиотеки Python устанавливаются в составе Служб машинного обучения SQL Server.

Вы загружаете модули и вызываете необходимые функции для создания и обучения модели с помощью хранимой процедуры SQL Server. Для модели требуются компоненты данных, разработанные на предыдущих занятиях. Наконец, вы сохраняете обученную модель в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Разделение примера данных на обучающий и проверочный наборы

1. Создайте хранимую процедуру с именем **PyTrainTestSplit**, чтобы разделить данные в таблице nyctaxi_sample на две части: nyctaxi_sample_training и nyctaxi_sample_testing. 

    Эта хранимая процедура уже должна быть создана. Но если это не так, ее можно создать, выполнив следующий код:

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

2. Чтобы разделить данные с помощью пользовательского разбиения, выполните хранимую процедуру и введите целое число, представляющее процент данных, выделенных для обучающего набора. Например, следующая инструкция выделит в обучающий набор 60 % данных.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Создание модели логистической регрессии

После подготовки данных их можно использовать для обучения модели. Для этого вызывается хранимая процедура, которая выполняет некоторый код Python, принимая таблицу обучающих данных в качестве входных данных. В этом руководстве вы создадите две модели. Обе модели будут использовать двоичную классификацию.

+ Хранимая процедура **PyTrainScikit** создает модель прогнозирования чаевых с помощью пакета **scikit-learn**.
+ Хранимая процедура **TrainTipPredictionModelRxPy** создает модель прогнозирования чаевых с помощью пакета **revoscalepy**.

Эта хранимая процедура использует указанные входные данные для создания и обучения модели логистической регрессии. Весь код Python находится в системной хранимой процедуре [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Чтобы упростить повторное обучение модели на основе новых данных, можно поместить вызов sp_execute_external_script в другую хранимую процедуру и передать новые обучающие данные в качестве параметра. В этом разделе описаны этапы этого действия.

### <a name="pytrainscikit"></a>PyTrainScikit

1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] откройте новое окно **Запрос** и выполните приведенную ниже инструкцию, чтобы создать хранимую процедуру **PyTrainScikit**.  Поскольку хранимая процедура уже включает в себя определение входных данных, указывать входной запрос не требуется.

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

2. Выполните следующие инструкции SQL, чтобы вставить обученную модель в таблицу nyc\_taxi_models.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Обработка данных и компоновка модели может занять несколько минут. Сообщения, которые должны передаваться в поток **stdout** Python, отображаются в окне **Сообщения** среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Пример:

    *Сообщения STDOUT из внешнего сценария:* 
  *C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Откройте таблицу *nyc\_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561....*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

В этой хранимой процедуре используется пакет **revoscalepy**, который является новым пакетом для Python. Он содержит объекты, преобразования и алгоритмы, аналогичные тем, которые содержатся в пакете **RevoScaleR** для языка R. 

С помощью **revoscalepy** можно создавать удаленные контексты вычислений, перемещать данные между контекстами вычислений, преобразовывать данные и обучать прогнозные модели с помощью популярных алгоритмов, таких как логистическая и линейная регрессия, деревья принятия решений и др. Дополнительные сведения см. в статьях [Модуль revoscalepy в SQL Server](../python/ref-py-revoscalepy.md) и [Справочник по функции revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] откройте новое окно **Запрос** и выполните приведенную ниже инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelRxPy_.  Поскольку хранимая процедура уже включает в себя определение входных данных, указывать входной запрос не требуется.

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

    В рамках обучения модели эта хранимая процедура выполняет следующие действия:

    - Запрос SELECT применяет пользовательскую скалярную функцию _fnCalculateDistance_ для вычисления прямого расстояния между местами посадки и высадки. Результаты выполнения запроса сохраняются во входной переменной Python по умолчанию `InputDataset`.
    - Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик: _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
    - Обученная модель сериализуется и сохраняется в переменной Python `logitObj`. С помощью ключевого слова OUTPUT T-SQL можно добавить переменную в качестве выходных данных хранимой процедуры. На следующем шаге эта переменная используется для вставки двоичного кода модели в таблицу базы данных _nyc_taxi_models_. Этот механизм упрощает хранение и повторное использование моделей.

2. Выполните хранимую процедуру следующим образом, чтобы вставить обученную модель **revoscalepy** в таблицу *nyc_taxi_models*.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Обработка данных и компоновка модели может занять некоторое время. Сообщения, которые должны передаваться в поток **stdout** Python, отображаются в окне **Сообщения** среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Пример:

    *Сообщения STDOUT из внешнего сценария:* 
  *C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Откройте таблицу *nyc_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *revoscalepy_model* *0x8003637265766F7363616c....*

На следующем шаге вы используете обученные модели для создания прогнозов.

## <a name="next-step"></a>Следующий шаг

[Прогнозирования с помощью встроенного кода Python в хранимой процедуре](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
