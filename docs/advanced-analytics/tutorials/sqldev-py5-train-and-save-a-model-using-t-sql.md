---
title: Обучение и сохранение модели Python с помощью T-SQL
description: Учебник по Python, демонстрирующий обучение и сохранение модели с помощью Transact-SQL на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 85115d55f10ebafde4fe2da9c0311425c5e870dc
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715343"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Обучение и сохранение модели Python с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья является частью руководства, [в базе данных Python Analytics для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы узнаете, как обучить модель машинного обучения с помощью пакетов Python **scikit-** Learning и **revoscalepy**. Эти библиотеки Python уже установлены с SQL Server Службы машинного обучения.

Вы загружаете модули и вызываете необходимые функции для создания и обучения модели с помощью хранимой процедуры SQL Server. Для модели требуются функции данных, разработанные на предыдущих занятиях. Наконец, вы сохраняете обученную модель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в таблице.
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Разделение образца данных на обучающие и проверочные наборы

1. Создайте хранимую процедуру с именем **питраинтестсплит** , чтобы разделить данные в таблице nyctaxi_sample на две части: nyctaxi_sample_training и nyctaxi_sample_testing. 

    Эта хранимая процедура уже должна быть создана для вас, но можно выполнить следующий код, чтобы создать его:

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

2. Чтобы разделить данные с помощью пользовательского разбиения, выполните хранимую процедуру и введите целое число, представляющее процент данных, выделенных для обучающего набора. Например, следующая инструкция выделит в обучающий набор 60% данных.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Создание модели логистической регрессии

После подготовки данные можно использовать для обучения модели. Это делается путем вызова хранимой процедуры, которая запускает некоторый код Python, принимая в качестве входных данных таблицу обучающих данными. В этом руководстве вы создадите две модели — обе модели двоичной классификации:

+ Хранимая процедура **питраинсЦикит** создает модель прогнозирования TIP с помощью пакета **scikit-учиться** .
+ Хранимая процедура **траинтиппредиктионмоделркспи** создает модель прогнозирования TIP с помощью пакета **revoscalepy** .

Каждая хранимая процедура использует входные данные, которые вы предоставляете для создания и обучения модели логистической регрессии. Весь код Python упаковывается в системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Чтобы упростить переобучение модели на новых данных, необходимо создать оболочку вызова sp_execute_exernal_script в другой хранимой процедуре и передать новые обучающие данные в качестве параметра. Этот раздел поможет вам выполнить этот процесс.

### <a name="pytrainscikit"></a>питраинсЦикит

1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте новое окно **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру **питраинсЦикит**.  Хранимая процедура содержит определение входных данных, поэтому не нужно указывать входной запрос.

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

2. Выполните следующие инструкции SQL, чтобы вставить обученную модель в таблицу\_Нью taxi_models.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Обработка данных и подгонка модели может занять несколько минут. Сообщения, которые будут переданы в поток **stdout** Python, отображаются в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]окне **сообщения** в. Пример:

    *Сообщения stdout из внешнего скрипта:* 
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Откройте таблицу *Нью\_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561....*

### <a name="traintippredictionmodelrxpy"></a>траинтиппредиктионмоделркспи

Эта хранимая процедура использует новый пакет **revoscalepy** , который является новым пакетом для Python. Он содержит объекты, преобразования и алгоритмы, аналогичные указанным для пакета **RevoScaleR** языка R. 

С помощью **revoscalepy**можно создавать удаленные контексты вычислений, перемещать данные между контекстами вычислений, преобразовывать данные и обучать прогнозные модели с помощью популярных алгоритмов, таких как логистическая и линейная регрессия, деревья принятия решений и многое другое. Дополнительные сведения см. [в разделе Модуль revoscalepy в](../python/ref-py-revoscalepy.md) справочнике по функциям SQL Server и [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте новое окно **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру _траинтиппредиктионмоделркспи_.  Поскольку хранимая процедура уже включает определение входных данных, не нужно указывать входной запрос.

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

    Эта хранимая процедура выполняет следующие действия в процессе обучения модели.

    - Запрос SELECT применяет пользовательскую скалярную функцию _fnCalculateDistance_ для вычисления прямого расстояния между расположениями подбора и выхода. Результаты запроса хранятся в входной переменной Python по умолчанию, `InputDataset`.
    - В качестве столбца *метки* или результата _используется переменная binary_ , а модель подходит для использования этих столбцов: _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
    - Обученная модель сериализуется и сохраняется в переменной `logitObj`Python. Добавляя выходные данные ключевого слова T-SQL, можно добавить переменную в качестве выходных данных хранимой процедуры. На следующем шаге эта переменная используется для вставки двоичного кода модели в таблицу базы данных _nyc_taxi_models_. Этот механизм упрощает хранение и повторное использование моделей.

2. Выполните хранимую процедуру, как показано ниже, чтобы вставить обученную модель **revoscalepy** в таблицу *nyc_taxi_models*.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Обработка данных и подгонка модели может занять некоторое время. Сообщения, которые будут переданы в поток **stdout** Python, отображаются в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]окне **сообщения** в. Пример:

    *Сообщения stdout из внешнего скрипта:* 
  *C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Откройте таблицу *nyc_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    *revoscalepy_model* *0x8003637265766F7363616c....*

На следующем шаге для создания прогнозов используются обученные модели.

## <a name="next-step"></a>Следующий шаг

[Выполнение прогнозов с помощью Python Embedded в хранимой процедуре](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
