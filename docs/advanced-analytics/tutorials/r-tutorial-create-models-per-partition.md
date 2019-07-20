---
title: Руководство по созданию, обучению и оценке моделей на основе секций в R
description: Сведения о моделировании, обучении и использовании секционированных данных, создаваемых динамически при использовании возможности моделирования на основе секций для машинного обучения SQL Server.
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/27/2019
ms.topic: tutorial
ms.author: davidph
author: dphansen
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8ceba61f4bdc22b4049453ed27245f09efe080b1
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345956"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Учебник. Создание моделей на основе секций в R на SQL Server
[!INCLUDE[appliesto-ssvnex-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В SQL Server 2019 моделирование на основе секций — это возможность создания и обучения моделей по секционированным данным. Для данных стратифицированной, которые естественным образом направлены в определенную схему классификации, такие как географические регионы, Дата и время, возраст или пол, можно выполнить сценарий для всего набора данных, с возможностью моделировать, обучать и оценивать секции, которые остаются без изменений. над всеми этими операциями. 

Моделирование на основе секций включено с помощью двух новых параметров в [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql):

+ **input_data_1_partition_by_columns**, который указывает столбец для секционирования.
+ **input_data_1_order_by_columns** указывает, какие столбцы нужно упорядочить. 

В этом руководстве рассматривается моделирование на основе секций с помощью классической модели НЬЮного такси и скрипта R. Столбец секционирования — это метод оплаты.

> [!div class="checklist"]
> * Секции основываются на типах платежей (5).
> * Создание и обучение моделей в каждой секции и сохранение объектов в базе данных.
> * Прогноз вероятности результатов TIP для каждой модели секционирования с использованием образцов данных, зарезервированных для этой цели.

## <a name="prerequisites"></a>Предварительные требования
 
Для работы с этим руководством необходимо следующее:

+ Достаточно системных ресурсов. Набор данных является большим, и операции обучения требуют больших ресурсов. Если это возможно, используйте систему, имеющую не менее 8 ГБ ОЗУ. Кроме того, можно использовать небольшие наборы данных, чтобы обойти ограничения ресурсов. Инструкции по сокращению набора данных являются встроенными. 

+ Средство для выполнения запросов T-SQL, например [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

+ [NYCTaxi_Sample. bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), который можно [скачать и восстановить](demo-data-nyctaxi-in-sql.md) в локальном экземпляре ядра СУБД. Размер файла составляет примерно 90 МБ.

+ SQL Server 2019 предварительный просмотр экземпляра ядра СУБД с интеграцией Службы машинного обучения и R.

Проверьте версию, выполнив **`SELECT @@Version`** как запрос T-SQL в средстве запроса. Выходные данные должны иметь значение "Microsoft SQL Server 2019 (CTP 2,4)-15,0. x".

Проверьте доступность пакетов R, выполнив правильный отформатированный список всех пакетов R, установленных в данный момент с экземпляром ядра СУБД.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

## <a name="connect-to-the-database"></a>Подключение к базе данных

Запустите Management Studio и подключитесь к экземпляру ядра СУБД. В обозревателе объектов убедитесь, что [база данных NYCTaxi_Sample](demo-data-nyctaxi-in-sql.md) существует. 

## <a name="create-calculatedistance"></a>Создание Калкулатедистанце

Демонстрационная база данных поставляется с скалярной функцией для вычисления расстояния, но наша хранимая процедура лучше работает с возвращающей табличное значение функцией. Выполните следующий скрипт, чтобы создать функцию **калкулатедистанце** , которая будет использоваться на [шаге обучения](#training-step) позже.

Чтобы убедиться, что функция создана, проверьте функции \Программабилити\функтионс\табле-валуед в базе данных **NYCTaxi_Sample** в обозревателе объектов.

```sql
USE NYCTaxi_sample
GO

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE FUNCTION [dbo].[CalculateDistance] (
    @Lat1 FLOAT
    ,@Long1 FLOAT
    ,@Lat2 FLOAT
    ,@Long2 FLOAT
    )
    -- User-defined function calculates the direct distance between two geographical coordinates.
RETURNS TABLE
AS
RETURN

SELECT COALESCE(3958.75 * ATAN(SQRT(1 - POWER(t.distance, 2)) / nullif(t.distance, 0)), 0) AS direct_distance
FROM (
    VALUES (CAST((SIN(@Lat1 / 57.2958) * SIN(@Lat2 / 57.2958)) + (COS(@Lat1 / 57.2958) * COS(@Lat2 / 57.2958) * COS((@Long2 / 57.2958) - (@Long1 / 57.2958))) AS DECIMAL(28, 10)))
    ) AS t(distance)
GO
 ```

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Определение процедуры создания и обучения моделей отдельных секций

В этом руководстве сценарий R создается в виде оболочки в хранимой процедуре. На этом шаге создается хранимая процедура, которая использует R для создания входного набора данных, построения модели классификации для прогнозирования результатов TIP, а затем сохраняет модель в базе данных.

Между входными параметрами, используемыми этим скриптом, вы увидите **input_data_1_partition_by_columns** и **input_data_1_order_by_columns**. Помните, что эти параметры являются механизмом, с помощью которого создается секционированное моделирование. Параметры передаются в качестве входных данных [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) для обработки секций с помощью внешнего скрипта, который выполняется один раз для каждой секции. 

Для этой хранимой процедуры [Используйте Parallel](#parallel) для ускорения выполнения.

После выполнения этого скрипта вы увидите **train_rxLogIt_per_partition** в процедурах \программабилити\сторед в базе данных **NYCTaxi_Sample** в обозревателе объектов. Также должна отобразиться новая таблица, используемая для хранения моделей: **dbo. nyctaxi_models**.

```sql
USE NYCTaxi_Sample
GO

CREATE
    OR

ALTER PROCEDURE [dbo].[train_rxLogIt_per_partition] (@input_query NVARCHAR(max))
AS
BEGIN
    DECLARE @start DATETIME2 = SYSDATETIME()
        ,@model_generation_duration FLOAT
        ,@model VARBINARY(max)
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name();

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    # Make sure InputDataSet is not empty. In parallel mode, if one thread gets zero data, an error occurs
    if (nrow(InputDataSet) > 0) {
    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    
    # build classification model to predict a tip outcome
    duration <- system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet))[3];

    # First, serialize a model to and put it into a database table
    modelbin <- as.raw(serialize(logitObj, NULL));

    # Create the data source. To reduce data size, add rowsPerRead=500000 to cut the dataset by half.
    ds <- RxOdbcData(table="ml_models", connectionString=connStr);

    # Store the model in the database
    model_name <- paste0("nyctaxi.", InputDataSet[1,]$payment_type);
    
    rxWriteObject(ds, model_name, modelbin, version = "v1",
    keyName = "model_name", valueName = "model_object", versionName = "model_version", overwrite = TRUE, serialize = FALSE);
    } 
    
    '
        ,@input_data_1 = @input_query
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@input_data_1_order_by_columns = N'passenger_count'
        ,@parallel = 1
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS NONE
END;
GO
```

<a name="parallel"></a>

### <a name="parallel-execution"></a>Параллельное выполнение

Обратите внимание, что входные данные [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) включают  **@parallel= 1**, используемую для параллельной обработки. В отличие от предыдущих выпусков, в SQL Server 2019 параметр  **@parallel= 1** обеспечивает более высокую подсказку оптимизатору запросов, что делает параллельное выполнение гораздо более вероятным результатом.

По умолчанию оптимизатор запросов работает  **@parallelс = 1** в таблицах, имеющих более 256 строк, но если эту операцию можно обработать явно, задав  **@parallel= 1** , как показано в этом скрипте.

> [!Tip]
> Для обучения воркоадс можно использовать **@parallel** с любым произвольным сценарием обучения, даже при использовании алгоритмов, отличных от Microsoft RX. Как правило, только алгоритмы RevoScaleR (с префиксом RX) предлагают параллелизм в сценариях обучения в SQL Server. Но с помощью нового параметра можно параллелизации скрипта, который вызывает функции, включая функции R с открытым исходным кодом, не разработанные специально для этой возможности. Это работает потому, что секции имеют сходство с определенными потоками, поэтому все операции, вызываемые в скрипте, выполняются по отдельности для каждого раздела в данном потоке.

<a name="training-step"></a>

## <a name="run-the-procedure-and-train-the-model"></a>Выполнение процедуры и обучение модели

В этом разделе Скрипт обучает модель, созданную и сохраненную на предыдущем шаге. В приведенных ниже примерах демонстрируются два подхода к обучению модели: использование всего набора данных или частичных данных. 

Этот шаг должен занять некоторое время. Обучение выполняется очень интенсивно и занимает много минут. Если системные ресурсы, в особенности память, недостаточно для загрузки, используйте подмножество данных. Во втором примере показан синтаксис.

```sql
--Example 1: train on entire dataset
EXEC train_rxLogIt_per_partition N'
SELECT payment_type, tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

```sql
--Example 2: Train on 20 percent of the dataset to expedite processing.
EXEC train_rxLogIt_per_partition N'
  SELECT tipped, payment_type, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample TABLESAMPLE (20 PERCENT) REPEATABLE (98074)
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

> [!NOTE]
> Если вы используете другие рабочие нагрузки, можно добавить `OPTION(MAXDOP 2)` к инструкции SELECT, если требуется ограничить обработку запросов только двумя ядрами.

## <a name="check-results"></a>Результаты проверки

Результат в таблице Models должен состоять из пяти разных моделей, основанных на пяти секциях, сегментированных пятью типами платежей. Модели находятся в источнике данных **ml_models** .

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Определение процедуры для прогнозирования результатов

Для оценки можно использовать одни и те же параметры. Следующий пример содержит скрипт R, который будет оценивать использование правильной модели для секции, которая в данный момент обрабатывается.

Как и ранее, создайте хранимую процедуру для упаковки кода R.

```sql
USE NYCTaxi_Sample
GO

-- Stored procedure that scores per partition. 
-- Depending on the partition being processed, a model specific to that partition will be used
CREATE
    OR

ALTER PROCEDURE [dbo].[predict_per_partition]
AS
BEGIN
    DECLARE @predict_duration FLOAT
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name()
        ,@input_query NVARCHAR(max);

    SET @input_query = 'SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance, payment_type
                          FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)
                          CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d'

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    if (nrow(InputDataSet) > 0) {

    #Get the partition that is currently being processed
    current_partition <- InputDataSet[1,]$payment_type;

    #Create the SQL query to select the right model
    query_getModel <- paste0("select model_object from ml_models where model_name = ", "''", "nyctaxi.",InputDataSet[1,]$payment_type,"''", ";")
    

    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
        
    #Define data source to use for getting the model
    ds <- RxOdbcData(sqlQuery = query_getModel, connectionString = connStr)

    # Load the model
    modelbin <- rxReadObject(ds, deserialize = FALSE)
    # unserialize model
    logitObj <- unserialize(modelbin);

    # predict tipped or not based on model
    predictions <- rxPredict(logitObj, data = InputDataSet, overwrite = TRUE, type = "response", writeModelVars = TRUE
        , extraVarsToWrite = c("payment_type"));        
    OutputDataSet <- predictions
    
    } else {
        OutputDataSet <- data.frame(integer(), InputDataSet[,]);        
    }
    '
        ,@input_data_1 = @input_query
        ,@parallel = 1
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS((
                tipped_Pred INT
                ,payment_type VARCHAR(5)
                ,tipped INT
                ,passenger_count INT
                ,trip_distance FLOAT
                ,trip_time_in_secs INT
                ,direct_distance FLOAT
                ));
END;
GO
```

## <a name="create-a-table-to-store-predictions"></a>Создание таблицы для хранения прогнозов

```sql
CREATE TABLE prediction_results (
    tipped_Pred INT
    ,payment_type VARCHAR(5)
    ,tipped INT
    ,passenger_count INT
    ,trip_distance FLOAT
    ,trip_time_in_secs INT
    ,direct_distance FLOAT
    );

TRUNCATE TABLE prediction_results
GO
```

## <a name="run-the-procedure-and-save-predictions"></a>Выполнение процедуры и сохранение прогнозов

```sql
INSERT INTO prediction_results (
    tipped_Pred
    ,payment_type
    ,tipped
    ,passenger_count
    ,trip_distance
    ,trip_time_in_secs
    ,direct_distance
    )
EXECUTE [predict_per_partition]
GO
```

## <a name="view-predictions"></a>Просмотр прогнозов

Поскольку прогнозы хранятся, можно выполнить простой запрос для возврата результирующего набора.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы использовали [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) для итерации операций по секционированным данным. Подробнее о вызове внешних скриптов в хранимых процедурах и использовании функций RevoScaleR см. в следующем руководстве.

> [!div class="nextstepaction"]
> [Пошаговое руководство для R и SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)

<!--
## Old intro

**(Not for production workloads)**

One of the more common approaches for executing R or Python code on SQL data is providing script as an input parameter to the [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure. In this CTP release, SQL Server 2019 adds new parameters to `sp_execute_external_script` to process partitions with the external script executing once for every partition:

| Parameter | Usage |
|-----------|-------|
| **input_data_1_partition_by_columns** | Specifies which columns to partition by. |
| **input_data_1_order_by_columns** | Specifies which columns to order by.  |

Partitions are an organizational mechanism for stratified data that naturally segments into a given classification scheme. Common examples include partitioning by geographic region, by date and time, by age or gender, and so forth. Given the existence of partitioned data, you might want to execute script over the entire data set, with the ability to model, train, and score partitions that remain intact over all these operations. Calling `sp_execute_external_script` with the new parameters allows you to do just that.

You can run this operation in parallel by combining `partition_by` with `@parallel`. If the input query can be parallelized, set `@parallel=1` as part of your arguments to `sp_execute_external_script`. By default, the query optimizer operates under `@parallel=1` on tables having more than 256 rows.

When the scenario is training, one advantage is that any arbitrary training script, even those using non-Microsoft-rx algorithms, can be parallelized by also using the @parallel parameter. Typically, you would have to use RevoScaleR algorithms (with the rx prefix) to obtain parallelism in training scenarios in SQL Server. But with the new parameter, you can parallelize a script that calls functions not specifically engineered with that capability.
-->
