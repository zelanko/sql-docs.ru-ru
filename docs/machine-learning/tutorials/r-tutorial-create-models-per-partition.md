---
title: Создание моделей на основе секций в R
description: Узнайте о моделировании, обучении и использовании секционированных данных, создаваемых динамически, с помощью возможностей моделирования на основе секций машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 04/30/2020
ms.topic: tutorial
ms.author: davidph
author: dphansen
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ec0323d35c05c34de763fbdece37546f7c8252df
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193667"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Руководство по Создание моделей на основе секций в R в SQL Server
[!INCLUDE [SQL Server 2016](../../includes/applies-to-version/sqlserver2016.md)]

В SQL Server 2019 моделирование на основе секций — это возможность создания и обучения моделей по секционированным данным. Для стратифицированных данных, которые естественным образом сегментируются в определенную классификационную схему, например по географическим регионам, дате и времени, возрасту или полу, вы можете выполнить скрипт для всего набора данных с возможностью моделирования, обучения и оценки по секциям, которые не затрагиваются всеми этими операциями. 

Моделирование на основе секций включается с помощью следующих двух новых параметров в [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Параметр **input_data_1_partition_by_columns** задает столбец для секционирования.
+ Параметр **input_data_1_order_by_columns** указывает, какие столбцы следует упорядочить. 

В этом руководстве рассматривается моделирование на основе секций с использованием классической выборки данных о работе такси в Нью-Йорке и скрипта R. Столбец секционирования — метод оплаты.

> [!div class="checklist"]
> * Построение секций по типам платежей (5).
> * Создание и обучение моделей в каждой секции и сохранение объектов в базе данных.
> * Прогнозирование вероятности исходов по каждой модели секционирования с использованием выборочных данных, зарезервированных для этой цели.

## <a name="prerequisites"></a>Предварительные требования
 
Для работы с этим учебником необходимо наличие следующих компонентов.

+ Достаточное количество системных ресурсов. Так как работа выполняется на большом наборе данных, операции обучения требуют много ресурсов. По возможности используйте систему с ОЗУ не менее 8 ГБ. Можно также попробовать использовать меньшие наборы данных, чтобы обойти ресурсные ограничения. Следуйте встроенным инструкциям по сокращению набора данных. 

+ Средство выполнения запросов T-SQL, например [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md).

+ Файл [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), который можно [скачать и восстановить](demo-data-nyctaxi-in-sql.md) в локальном экземпляре ядра СУБД. Размер файла составляет приблизительно 90 МБ.

+ Экземпляр ядра СУБД SQL Server 2019 со службами машинного обучения и интеграцией R.

+ В этом руководстве используется [петлевое соединение, устанавливаемое с SQL Server из сценария R через ODBC](../connect/loopback-connection.md). Поэтому необходимо [создать имя входа для SQLRUserGroup](../security/create-a-login-for-sqlrusergroup.md).

Проверьте версию, выполнив **`SELECT @@Version`** как запрос T-SQL в средстве выполнения запросов.

Проверьте доступность пакетов R путем получения правильно отформатированного списка всех пакетов R, установленных в текущий момент с вашим экземпляром ядра СУБД:

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

Запустите Management Studio и подключитесь к экземпляру ядра СУБД. Убедитесь, что в обозревателе объектов имеется [база данных NYCTaxi_Sample](demo-data-nyctaxi-in-sql.md). 

## <a name="create-calculatedistance"></a>Создание функции CalculateDistance

Демонстрационная база данных предоставляется со скалярной функцией для вычисления расстояния, но наша хранимая процедура лучше работает с функцией с табличным значением. Чтобы создать функцию **CalculateDistance**, которая позднее будет использоваться на [этапе обучения](#training-step), выполните следующий скрипт.

Чтобы убедиться, что функция создана, проверьте раздел \Programmability\Functions\Table-valued Functions в ветке базы данных **NYCTaxi_Sample** в обозревателе объектов.

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

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Определение процедуры создания и обучения моделей для отдельных секций

В этом учебнике сценарий R заключается в хранимую процедуру. На этом шаге создается хранимая процедура, которая с использованием R создает входной набор данных, строит модель классификации для прогнозирования результатов, а затем сохраняет эту модель в базе данных.

В качестве входных параметров, используемых этим скриптом, вы увидите **input_data_1_partition_by_columns** и **input_data_1_order_by_columns**. Напомним, что эти параметры и есть механизм, с помощью которого создается секционированное моделирование. Эти параметры передаются в качестве входных данных в [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для обработки секций с помощью данного внешнего скрипта, который выполняется один раз для каждой секции. 

Чтобы эта хранимая процедура выполнялась быстрее, [используйте параллелизм](#parallel).

После выполнения этого скрипта в обозревателе объектов в ветке базы данных **NYCTaxi_Sample** в разделе \Programmability\Stored Procedures появится **train_rxLogIt_per_partition**. Также должна появиться новая таблица, используемая для хранения моделей: **dbo.nyctaxi_models**.

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

Обратите внимание, что среди входных данных для скрипта [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) имеется параметр `@parallel=1`. Он используется для включения параллельной обработки. В отличие от предыдущих выпусков, в SQL Server 2019 параметр `@parallel=1` обеспечивает более строгое указание оптимизатору запросов, что делает параллельное выполнение гораздо более вероятным результатом.

По умолчанию в рамках `@parallel=1` оптимизатор запросов стремится работать в таблицах, имеющих более 256 строк, но это можно задать явно, установив `@parallel=1`, как показано в данном скрипте.

> [!Tip]
> Для рабочих нагрузок обучения можно использовать `@parallel` с любым произвольным скриптом обучения, даже при использовании алгоритмов, отличных от Microsoft RX. Как правило, в SQL Server параллелизм в скриптах обучения предусмотрен только в алгоритмах RevoScaleR (с префиксом RX). Но с помощью нового параметра можно параллелизовать скрипт, который вызывает функции, не разрабатывавшиеся специально с включением этой возможности (в том числе функции R с открытым исходным кодом). Это работает потому, что секции имеют сходство с определенными потоками,так что все операции, вызываемые в скрипте, выполняются для каждого раздела по отдельности, в выделенном `thread.`<a name="training-step"></a>

## <a name="run-the-procedure-and-train-the-model"></a>Выполнение процедуры и обучение модели

В этом разделе скрипт обучает модель, созданную и сохраненную на предыдущем шаге. В приведенных ниже примерах демонстрируются два подхода к обучению модели: с использованием всего набора данных или частичных данных. 

Этот шаг займет некоторое время. Обучение требует больших вычислительных ресурсов и выполняется много минут. Если системных ресурсов, в особенности памяти, недостаточно для этой нагрузки, используйте подмножество данных. Во втором примере показан синтаксис.

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
> Если одновременно выполняются и другие рабочие нагрузки, можно ограничить до двух число ядер, используемых для обработки запросов, добавив `OPTION(MAXDOP 2)` в инструкцию SELECT.

## <a name="check-results"></a>Проверка результатов

В результате в таблице models должно появиться пять разных моделей, основанных на пяти секциях, сегментированных по пяти типам платежей. Модели находятся в источнике данных **ml_models**.

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Задание процедуры для прогнозирования результатов

Для оценки можно использовать те же параметры. В следующем примере приведен скрипт R, оценивающий использование правильной модели для секции, которая в данный момент обрабатывается.

Как и ранее, создайте хранимую процедуру для включение в нее кода R.

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

Так как прогнозы сохраняются, можно выполнить простой запрос для возврата результатов.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы использовали скрипт [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для выполнения цикла операций по секционированным данным. Более подробно вызов внешних скриптов в хранимых процедурах и использование функций RevoScaleR рассматривается в следующем учебнике.

> [!div class="nextstepaction"]
> [Пошаговое руководство для R и SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)