---
title: "Развертывание модели R и использовать его в SQL (Пошаговое руководство) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b0514d7b32eec5899ab24450bdfc0c38f141fee
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>Развертывание модели R и использовать его в SQL

На этом занятии вы использовать R-модели в рабочей среде путем вызова обученной модели из хранимой процедуры. Затем можно вызвать хранимую процедуру из R или любом языке программирования приложения, который поддерживает [!INCLUDE[tsql](../../includes/tsql-md.md)] (например, C#, Java, Python, т. д.), для использования модели для создания прогнозов на новый наблюдения.

Этот образец демонстрирует два наиболее распространенных способа использования модели в оценки:

- **Режим оценки пакета** используется, когда требуется создать несколько прогнозов очень быстро, передавая SQL-запроса или таблицы в качестве входных данных. Таблица результатов возвращается, который может вставить непосредственно в таблицу или записать в файл.

- **Режим отдельных количественной оценки** используется, когда необходимо создать по одному прогнозу. Можно передать набор отдельных значений в хранимую процедуру. Значения соответствуют возможностям в модели в модели используется для создания прогноза, или создать другой результат, например значение вероятности. Затем можно вернуть значение приложением или пользователем.

## <a name="batch-scoring"></a>Массовая оценка

Хранимая процедура для массовой оценки был создан при выполнении сценария PowerShell изначально. Эта хранимая процедура, *PredictTipBatchMode*, делает следующее:

- получает набор входных данных в виде запроса SQL;
- вызывает обученную модель логистической регрессии, которая была сохранена на предыдущем занятии;
- Прогнозирует вероятность, что драйвер возвращает любое ненулевое значение подсказки

1. Внимательно изучите скрипт для хранимой процедуры *PredictTipBatchMode*. Он иллюстрирует несколько аспектов ввода модели в эксплуатацию с помощью служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].
  
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

    + Использование инструкции SELECT для вызова хранимых модели из таблицы SQL. Модели извлекаются из таблицы как **varbinary(max)** данные, хранящиеся в переменной SQL  _@lmodel2_ и переданный в качестве параметра *mod* системе хранятся процедура [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Данные, используемые в качестве входных данных для оценки определяется как SQL-запроса и хранятся в виде строки в SQL-переменной  _@input_ . По мере извлечения данных из базы данных хранится в кадр данных называется *InputDataSet*, — просто имя по умолчанию для входных данных для [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) процедуру; можно определить другое имя переменной, при необходимости с помощью параметра   *_@input_data_1_name_*  .

    + Для формирования оценок хранимая процедура вызывает функцию `rxPredict` из библиотеки **RevoScaleR** .

    + Возвращаемое значение *Оценка*, — это вероятность данной модели, что драйвер возвращает подсказку. При необходимости можно легко применить какой-либо фильтр возвращаемые значения для классификации возвращаемые значения «совет» и «не совет» групп.  Например с вероятностью меньше 0,5 означает, что совет маловероятно.
  
2.  Чтобы вызвать хранимую процедуру в пакетном режиме, следует определить запрос, необходимый в качестве входных данных для хранимой процедуры. Следующий запрос SQL; его можно запустить в среде SSMS, чтобы убедиться, что он работает.

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

3. Используйте следующий код R для создания входные строки из SQL-запроса:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Для выполнения хранимой процедуры из R, вызовите **sqlQuery** метод **RODBC** пакета и использовать соединение SQL `conn` , определенного ранее:

    ```R
    sqlQuery (conn, q);
    ```

    Если появляется сообщение об ошибке ODBC, Проверьте синтаксис запроса, и что у вас есть нужное число кавычки. 
    
    Если появляется ошибка разрешения, убедитесь, что имя входа имеет возможность выполнения хранимой процедуры.

## <a name="single-row-scoring"></a>Оценки одной строки

При вызове модели для прогнозирования на основе по строкам, можно передать набор значений, которые представляют компоненты для каждого отдельного случая. Хранимая процедура возвращает один прогноз или вероятности. 

Хранимая процедура *PredictTipSingleMode* демонстрирует этот подход. Она принимает в качестве ввода несколько параметров, представляющих значения компонента (например, пассажира count и trip расстояние), оценок этих компонентов, с использованием хранимых R-модели и выводит совет по вероятности.

1. Если хранимая процедура *PredictTipSingleMode* не был создан исходный сценарий PowerShell, можно выполнить следующую инструкцию Transact-SQL, чтобы создать ее.

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

2. В SQL Server Management Studio можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** процедуры (или **EXECUTE**) для вызова хранимой процедуры и передать его входные данные, необходимые. Например запустите эту инструкцию в среде Management Studio:

    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Переданные здесь значения представляют, соответственно, для переменных _пассажира\_число_, _trip_distance_, _trip\_время\_в\_сек_, _раскладки\_широты_, _раскладки\_долготы_, _dropoff\_широты_, и _dropoff\_долготы_.

3. Чтобы запустить этот же вызов из кода R, просто определить переменной R, который содержит вызов всю хранимую процедуру, похожее на следующее:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Переданные здесь значения представляют, соответственно, для переменных _пассажира\_число_, _trip\_расстояние_, _trip\_время\_в\_сек_, _раскладки\_широты_, _раскладки\_долготы_, _dropoff\_ Широта_, и _dropoff\_долготы_.

4. Вызовите `sqlQuery` (из **RODBC** пакетов) и передайте строку подключения, а также строковую переменную, содержащую вызов хранимой процедуры.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > Средства R для Visual Studio (RTVS) обеспечивает значительные интеграцию с SQL Server и R. См. в статье Дополнительные примеры использования RODBC с подключение к SQL Server: [работы с SQL Server и R](https://docs.microsoft.com/en-us/visualstudio/rtvs/sql-server)

## <a name="summary"></a>Сводка

Теперь, когда вы узнали, как работать с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных и сохранения обученных моделей R для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], относительно легко создавать новые модели на основе этого набора данных. Например вы можете создать эти дополнительные модели:

- модель регрессии, прогнозирующая размер чаевых;

- Модель мультиклассовой классификации, которая прогнозирует ли совет больших, среднего и малого

Мы также рекомендуем просмотреть некоторые из представленных дополнительных примеров и ресурсов:

+ [Сценарии и шаблоны решений для обработки и анализа данных](data-science-scenarios-and-solution-templates.md)

+ [Дополнительные аналитические функции в базе данных для разработчиков SQL (руководство)](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [Дополнительные ресурсы](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>Предыдущее занятие

[Построить модель R и сохранить его в SQL Server](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>Следующие шаги

[Учебники по SQL Server R](sql-server-r-tutorials.md)

[Создание хранимой процедуры, с помощью sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
