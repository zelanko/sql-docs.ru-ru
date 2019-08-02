---
title: Развертывание модели R для прогнозов на SQL Server
description: Учебник, показывающий, как развернуть модель R на SQL Server для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: aba6990fbed5b24d63d4ab5c16e192718aeff305
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714680"
---
# <a name="deploy-the-r-model-and-use-it-in-sql-server-walkthrough"></a>Развертывание модели R и ее использование в SQL Server (пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

На этом занятии вы узнаете, как развертывать модели R в рабочей среде, вызывая обученную модель из хранимой процедуры. Хранимую процедуру можно вызвать из R или любого языка программирования приложений, который поддерживает [!INCLUDE[tsql](../../includes/tsql-md.md)] (например C#, Java, Python и т. д.) и использовать эту модель для прогнозирования новых наблюдений.

В этой статье показаны два наиболее распространенных способа использования модели в оценке.

> [!div class="checklist"]
> * **Режим пакетной оценки** формирует несколько прогнозов
> * **Отдельный режим оценки** создает прогнозы по одному за раз

## <a name="batch-scoring"></a>Пакетная Оценка

Создайте хранимую процедуру *PredictTipBatchMode*, которая создает несколько прогнозов, передавая запрос SQL или таблицу в качестве входных данных. Возвращается таблица результатов, которая может быть вставлена непосредственно в таблицу или записана в файл.

- получает набор входных данных в виде запроса SQL;
- вызывает обученную модель логистической регрессии, которая была сохранена на предыдущем занятии;
- Прогнозирует вероятность того, что драйвер получает любой ненулевой Совет

1. В Management Studio откройте новое окно запроса и выполните следующий скрипт T-SQL, чтобы создать хранимую процедуру PredictTipBatchMode.
  
    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipBatchMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @input nvarchar(max)
    AS
    BEGIN
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);
      EXEC sp_execute_external_script @language = N'R',
         @script = N'
           mod <- unserialize(as.raw(model));
           print(summary(mod))
           OutputDataSet<-rxPredict(modelObject = mod,
             data = InputDataSet,
             outData = NULL,
             predVarNames = "Score", type = "response",
             writeModelVars = FALSE, overwrite = TRUE);
           str(OutputDataSet)
           print(OutputDataSet)',
      @input_data_1 = @input,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

    + Для вызова хранимой модели из таблицы SQL используется инструкция SELECT. Модель извлекается из таблицы как данные типа **varbinary (max)** , хранятся в переменной  _\@SQL lmodel2_и передается в качестве параметра *Mod* в системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Данные, используемые в качестве входных данных для оценки, определяются как SQL-запрос и хранятся в виде строки  _\@_ в входных данных переменной SQL. По мере извлечения данных из базы данных они хранятся в кадре данных с именем *InputDataSet*, который является просто именем по умолчанию для входных данных в процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) . При необходимости можно определить другое имя переменной с помощью параметра  *_\@input_data_1_name_* .

    + Для создания оценок хранимая процедура вызывает функцию rxPredict из библиотеки **RevoScaleR** .

    + Возвращаемое значение, *Score*, является вероятностью, заданным в модели, этот драйвер получает подсказку. При необходимости можно легко применить какой либо фильтр к возвращаемым значениям, чтобы классифицировать возвращаемые значения в группы "TIP" и "No TIP".  Например, вероятность менее 0,5 означает, что подсказка маловероятно.
  
2.  Чтобы вызвать хранимую процедуру в пакетном режиме, необходимо определить запрос, необходимый в качестве входных данных для хранимой процедуры. Ниже приведен SQL-запрос, который можно запустить в среде SSMS, чтобы убедиться, что он работает.

    ```sql
    SELECT TOP 10
      a.passenger_count AS passenger_count,
      a.trip_time_in_secs AS trip_time_in_secs,
      a.trip_distance AS trip_distance,
      a.dropoff_datetime AS dropoff_datetime,
      dbo.fnCalculateDistance( pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance
      FROM 
        (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude 
        FROM nyctaxi_sample)a 
      LEFT OUTER JOIN
      ( SELECT medallion, hack_license, pickup_datetime
      FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b
      ON a.medallion=b.medallion
      AND a.hack_license=b.hack_license
      AND a.pickup_datetime=b.pickup_datetime
      WHERE b.medallion is null
    ```

3. Используйте этот код R для создания входной строки из SQL запроса:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @input = ", input, sep="");
    ```

4. Чтобы запустить хранимую процедуру из R, вызовите метод **sqlQuery** пакета **RODBC** и используйте ранее определенное подключение `conn` SQL.

    ```R
    sqlQuery (conn, q);
    ```

    При возникновении ошибки ODBC проверьте наличие синтаксических ошибок и наличие правильного числа кавычек. 
    
    При получении ошибки разрешений убедитесь, что у имени входа есть возможность выполнения хранимой процедуры.

## <a name="single-row-scoring"></a>Оценка одной строки

Отдельный режим оценки создает прогнозы по одному за раз, передавая набор отдельных значений в хранимую процедуру в качестве входных данных. Значения соответствуют компонентам модели, которые модель использует для создания прогноза, или создают другой результат, например значение вероятности. Затем это значение можно вернуть приложению или пользователю.

При вызове модели для прогнозирования по строкам передается набор значений, представляющих функции для каждого отдельного случая. Затем хранимая процедура возвращает один прогноз или вероятность. 

Этот подход демонстрируется в хранимой процедуре *PredictTipSingleMode* . Он принимает в качестве входных данных несколько параметров, представляющих значения функций (например, количество пассажиров и расстояние поездок), оценивает эти функции с помощью хранимой модели R и выводит вероятность TIP.

1. Выполните следующую инструкцию Transact-SQL, чтобы создать хранимую процедуру.

    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipSingleMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,
    @trip_distance float = 0,
    @trip_time_in_secs int = 0,
    @pickup_latitude float = 0,
    @pickup_longitude float = 0,
    @dropoff_latitude float = 0,
    @dropoff_longitude float = 0
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs, @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)'
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);

      EXEC sp_execute_external_script @language = N'R',  @script = N'
            mod <- unserialize(as.raw(model));
            print(summary(mod))
            OutputDataSet<-rxPredict(
              modelObject = mod,
              data = InputDataSet,
              outData = NULL,
              predVarNames = "Score",
              type = "response",
              writeModelVars = FALSE,
              overwrite = TRUE);
            str(OutputDataSet)
            print(OutputDataSet)
            ',
      @input_data_1 = @inquery,
      @params = N'
      -- passthrough columns
      @model varbinary(max) ,
      @passenger_count int ,
      @trip_distance float ,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      -- mapped variables
      @model = @lmodel2 ,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance ,
      @trip_time_in_secs=@trip_time_in_secs ,
      @pickup_latitude=@pickup_latitude ,
      @pickup_longitude=@pickup_longitude ,
      @dropoff_latitude=@dropoff_latitude ,
      @dropoff_longitude=@dropoff_longitude
      WITH RESULT SETS ((Score float));
    END
    ```

2. В SQL Server Management Studio можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] процедуру **exec** (или **EXECUTE**) для вызова хранимой процедуры и передать ей необходимые входные данные. Например, попробуйте выполнить эту инструкцию в Management Studio:

    ```sql
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Передаваемые здесь значения — это, соответственно, для переменных _\_пассажиров Count_, _trip_distance_, _время\_\_поездки в\__ секунду, широты _отправки\__ , _Долгота отправки\__ , _высадки\_Широта_и _высадки\_Долгота_.

3. Чтобы выполнить тот же вызов из кода R, достаточно определить переменную R, содержащую вызов всего хранимой процедуры, как показано ниже:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Передаваемые здесь значения — это, соответственно, для переменных _пассажиров\_Count_, _расстояние поездок\__ , _время\_\_поездки в\__ секунду, _Отправка\_ Широта_, _Долгота отправки\__ , _высадки\_Широта_и _высадки\_Долгота_.

4. Вызовите `sqlQuery` (из пакета **RODBC** ) и передайте строку подключения вместе со строковой переменной, содержащей вызов хранимой процедуры.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > Инструменты R для Visual Studio (RTVS) обеспечивает высокую интеграцию с SQL Server и R. Дополнительные примеры использования RODBC с подключением к SQL Server см. в этой статье: [Работа с SQL Server и R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы узнали, как работать с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данными и сохранять обученные модели [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]R в, создание новых моделей на основе этого набора данных должно быть сравнительно простым. Например, вы можете попытаться создать следующие дополнительные модели:

+ модель регрессии, прогнозирующая размер чаевых;
+ Модель многоклассовой классификации, которая прогнозирует, является ли tip большой, средней или маленькой

Вам также может потребоваться изучить следующие дополнительные примеры и ресурсы:

+ [Сценарии и шаблоны решений для обработки и анализа данных](data-science-scenarios-and-solution-templates.md)
+ [Дополнительные аналитические функции в базе данных для разработчиков SQL (руководство)](sqldev-in-database-r-for-sql-developers.md)
+ [Machine Learning Server руководства](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)
+ [Machine Learning Server дополнительных ресурсов](https://docs.microsoft.com//machine-learning-server/resources-more)
