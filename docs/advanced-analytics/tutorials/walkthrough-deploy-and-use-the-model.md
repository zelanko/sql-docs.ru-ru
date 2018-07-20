---
title: Развертывание модели R и использовать его в SQL (Пошаговое руководство) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a5d8b7ac8bd36a6ce76b895b2dde4a07f5ea96
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085356"
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>Развертывание модели R и использовать его в SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

На этом занятии вы использовать R-модели в рабочей среде, путем вызова обученной модели из хранимой процедуры. Затем можно вызвать хранимую процедуру из R или любого прикладного языка программирования, поддерживающий [!INCLUDE[tsql](../../includes/tsql-md.md)] (например, C#, Java, Python, и т.д.), чтобы использовать модель для создания прогнозов на основе новых наблюдений.

В этом примере демонстрируется два наиболее распространенных способа использования модели в среде оценки:

- **Режим пакетной оценки** используется, когда вам нужно создать несколько прогнозов очень быстро, передав SQL-запроса или таблицы в качестве входных данных. Таблица результатов возвращается, который может вставлять непосредственно в таблицу или записать в файл.

- **Режим индивидуальной оценки** используется, когда необходимо создать по одному прогнозу в каждый. Передайте набор отдельных значений в хранимую процедуру. Значения, соответствующие функции в модели и модели используется для создания прогноза, или создать еще один результат, например, значение вероятности. Это значение затем можно вернуться к приложения или пользователя.

## <a name="batch-scoring"></a>Пакетная оценка

Хранимая процедура для пакетной оценки был создан при первом выполнении сценария PowerShell. Эта хранимая процедура, *PredictTipBatchMode*, делает следующее:

- получает набор входных данных в виде запроса SQL;
- вызывает обученную модель логистической регрессии, которая была сохранена на предыдущем занятии;
- Прогнозирует вероятность того, что драйвер возвращает любое ненулевое значение подсказки

1. Внимательно изучить скрипт для хранимой процедуры, *PredictTipBatchMode*. Он иллюстрирует несколько аспектов ввода модели в эксплуатацию с помощью служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].
  
    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]
    @input nvarchar(max)
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

    + Данные, используемые в качестве входных данных для оценки определяется как SQL-запрос и храниться в виде строки в переменной SQL  _\@ввода_. Данные извлекаются из базы данных, сохраняются в кадре данных *InputDataSet*, это просто имя по умолчанию для входных данных [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) процедуры; вы можете определить другое имя переменной, при необходимости с помощью параметра   *_\@input_data_1_name_*.

    + Для формирования оценок хранимая процедура вызывает функцию `rxPredict` из библиотеки **RevoScaleR** .

    + Возвращаемое значение *Оценка*, — это вероятность, учитывая модель, этот драйвер возвращает совет. При необходимости можно легко применить определенный фильтр к возвращаемым значениям, чтобы разделить возвращаемые значения «совет» и «без чаевых».  Например вероятность менее 0,5 означает вряд ли совет.
  
2.  Чтобы вызвать хранимую процедуру в пакетном режиме, следует определить запрос, необходимый в качестве входных данных в хранимую процедуру. Ниже приведен запрос SQL; его можно запускать в SSMS, чтобы убедиться, что оно работает.

    ```SQL
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

    Если появится сообщение об ошибке ODBC, проверки синтаксиса запроса, и что у вас есть нужное число кавычки. 
    
    Если возникает ошибка разрешения, убедитесь, что имя входа имеет возможность выполнения хранимой процедуры.

## <a name="single-row-scoring"></a>Оценка одной строки

При вызове модели для прогнозирования на основе row-by-row, передается набор значений, представляющих функции для каждого отдельного случая. Хранимая процедура возвращает отдельный прогноз или вероятности. 

Хранимая процедура *PredictTipSingleMode* демонстрацией этого подхода. Она принимает в качестве входных данных несколько параметров, представляющих значения компонента (например, пассажиров count и расстояние поездки), оценивает эти характеристики с помощью хранимой модели R и выводит вероятность чаевых.

1. Если хранимая процедура *PredictTipSingleMode* не был создан с помощью начального сценария PowerShell, можно запустить следующую инструкцию Transact-SQL, чтобы создать ее сейчас.

    ```tsql
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

    ```SQL
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
    > Инструменты R для Visual Studio (RTVS) включают глубокая интеграция с SQL Server и R. См. в статье Дополнительные примеры использования RODBC с подключение к SQL Server: [работа с SQL Server и R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="summary"></a>Сводка

Теперь, когда вы узнали, как работать с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные и сохранять модели обучения R для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], он должен быть относительно легко создавать новые модели на основе этого набора данных. Например можно попытаться создать эти дополнительные модели:

- модель регрессии, прогнозирующая размер чаевых;

- Модель мультиклассовой классификации, которая прогнозирует, является ли совет больших, среднего и малого размера

Мы также рекомендуем просмотреть некоторые из представленных дополнительных примеров и ресурсов:

+ [Сценарии и шаблоны решений для обработки и анализа данных](data-science-scenarios-and-solution-templates.md)

+ [Дополнительные аналитические функции в базе данных для разработчиков SQL (руководство)](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [Дополнительные ресурсы](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>Предыдущее занятие

[Создание модели R и сохраните его в SQL Server](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>Следующие шаги

[Учебники по SQL Server R](sql-server-r-tutorials.md)

[Создание хранимой процедуры с помощью sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
