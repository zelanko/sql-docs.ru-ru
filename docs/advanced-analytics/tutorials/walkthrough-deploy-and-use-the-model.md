---
title: Развернуть модель R для прогнозирования на основе SQL Server — машинного обучения SQL Server
description: Учебник, в котором показано, как развернуть модель R в SQL Server для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: e79dd0bce559259863128de1d2490f0fd9197cf1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961697"
---
# <a name="deploy-the-r-model-and-use-it-in-sql-server-walkthrough"></a>Развертывание модели R и использовать его в SQL Server (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

На этом занятии вы научитесь развертывать модели R в рабочей среде путем вызова обученной модели из хранимой процедуры. Можно вызвать хранимую процедуру из R или любого прикладного языка программирования, поддерживающий [!INCLUDE[tsql](../../includes/tsql-md.md)] (такие как C#, Java, Python и т. д) и использование модели для создания прогнозов на основе новых наблюдений.

В этой статье показано два наиболее распространенных способа использования модели в среде оценки:

> [!div class="checklist"]
> * **Режим пакетной оценки** создает несколько прогнозов
> * **Режим индивидуальной оценки** создает по одному прогнозу в каждый

## <a name="batch-scoring"></a>Пакетная оценка

Создание хранимой процедуры, *PredictTipBatchMode*, который создает несколько прогнозов, передав в качестве входных данных в SQL-запрос или таблицу. Таблица результатов возвращается, который может вставлять непосредственно в таблицу или записать в файл.

- получает набор входных данных в виде запроса SQL;
- вызывает обученную модель логистической регрессии, которая была сохранена на предыдущем занятии;
- Прогнозирует вероятность того, что драйвер возвращает любое ненулевое значение подсказки

1. В среде Management Studio откройте новое окно запроса и выполните следующий сценарий T-SQL для создания PredictTipBatchMode хранимой процедуры.
  
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

    + Используйте инструкцию SELECT для вызова хранимой модели из таблицы SQL. Модель извлекается из нее, как **varbinary(max)** данных, которые хранятся в переменной SQL  _\@lmodel2_и передается в качестве параметра *mod* в систему Хранимая процедура [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Данные, используемые в качестве входных данных для оценки определяется как SQL-запрос и храниться в виде строки в переменной SQL  _\@ввода_. Данные извлекаются из базы данных, сохраняются в кадре данных *InputDataSet*, это просто имя по умолчанию для входных данных [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) процедуры; вы можете определить другое имя переменной, при необходимости с помощью параметра * _\@input_data_1_name_* .

    + Для формирования оценок, хранимая процедура вызывает функцию rxPredict из **RevoScaleR** библиотеки.

    + Возвращаемое значение *Оценка*, — это вероятность, учитывая модель, этот драйвер возвращает совет. При необходимости можно легко применить определенный фильтр к возвращаемым значениям, чтобы разделить возвращаемые значения «совет» и «без чаевых».  Например вероятность менее 0,5 означает вряд ли совет.
  
2.  Чтобы вызвать хранимую процедуру в пакетном режиме, следует определить запрос, необходимый в качестве входных данных в хранимую процедуру. Ниже приведен запрос SQL, который можно запустить в SSMS, чтобы убедиться, что оно работает.

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

3. Используйте следующий код R, чтобы создать входной строки из SQL-запроса:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Чтобы выполнить хранимую процедуру из R, вызовите **sqlQuery** метод **RODBC** упаковки и использовать подключение SQL `conn` , определенную ранее:

    ```R
    sqlQuery (conn, q);
    ```

    Если появится сообщение об ошибке ODBC, проверьте наличие синтаксических ошибок и что у вас есть нужное число кавычки. 
    
    Если возникает ошибка разрешения, убедитесь, что имя входа имеет возможность выполнения хранимой процедуры.

## <a name="single-row-scoring"></a>Оценка одной строки

Режим индивидуальной оценки создает одному прогнозу в каждый по одному, передавая набор отдельных значений в хранимую процедуру в качестве входных данных. Значения, соответствующие функции в модели и модели используется для создания прогноза, или создать еще один результат, например, значение вероятности. Это значение затем можно вернуться к приложения или пользователя.

При вызове модели для прогнозирования на основе row-by-row, передается набор значений, представляющих функции для каждого отдельного случая. Хранимая процедура возвращает отдельный прогноз или вероятности. 

Хранимая процедура *PredictTipSingleMode* демонстрацией этого подхода. Она принимает в качестве входных данных несколько параметров, представляющих значения компонента (например, пассажиров count и расстояние поездки), оценивает эти характеристики с помощью хранимой модели R и выводит вероятность чаевых.

1. Выполните следующую инструкцию Transact-SQL для создания хранимой процедуры.

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

2. В SQL Server Management Studio, можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** процедуры (или **EXECUTE**) для вызова хранимой процедуры и передачи ей необходимые входные данные. Например попробуйте, выполнить эту инструкцию в среде Management Studio:

    ```sql
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Здесь передаются значения являются, соответственно, для переменных _пассажиров\_число_, _trip_distance_, _trip\_время\_в\_сек_, _pickup\_широты_, _pickup\_долготы_, _высадки\_широты_, и _высадки\_долготы_.

3. Чтобы выполнить этот же вызов из кода R, просто Определите переменную R, содержащую весь вызов хранимой процедуры, похожее на следующее:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Здесь передаются значения являются, соответственно, для переменных _пассажиров\_число_, _trip\_расстояние_, _trip\_время\_в\_сек_, _pickup\_широты_, _pickup\_долготы_, _высадки\_ Широта_, и _высадки\_долготы_.

4. Вызовите `sqlQuery` (из **RODBC** пакета) и передать строку подключения, а также строковую переменную, содержащую вызов хранимой процедуры.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > Инструменты R для Visual Studio (RTVS) включают глубокая интеграция с SQL Server и R. См. в статье Дополнительные примеры использования RODBC с подключение к SQL Server: [Работа с SQL Server и R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы узнали, как работать с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные и сохранять модели обучения R для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], он должен быть относительно легко создавать новые модели на основе этого набора данных. Например можно попытаться создать эти дополнительные модели:

+ модель регрессии, прогнозирующая размер чаевых;
+ Модель мультиклассовой классификации, которая прогнозирует, является ли совет больших, среднего и малого размера

Можно также исследовать эти дополнительные примеры и ресурсы:

+ [Сценарии и шаблоны решений для обработки и анализа данных](data-science-scenarios-and-solution-templates.md)
+ [Дополнительные аналитические функции в базе данных для разработчиков SQL (руководство)](sqldev-in-database-r-for-sql-developers.md)
+ [Machine Learning Server руководства Руководство](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)
+ [Дополнительные ресурсы сервера машинного обучения](https://docs.microsoft.com//machine-learning-server/resources-more)
