---
title: "Урок 6: R-модели ввода в эксплуатацию | Документы Microsoft"
ms.custom: 
ms.date: 08/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 52b05828-11f5-4ce3-9010-59c213a674d1
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0fbdebc582650b0bd524d583d936848ae42e5f6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-6-operationalize-the-r-model"></a>Урок 6: R-модели ввода в эксплуатацию

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом шаге вы научитесь *ввода в эксплуатацию* модели с помощью хранимой процедуры. Эта хранимая процедура может вызываться напрямую другими приложениями для создания прогнозов на основе новых наблюдений. В примере демонстрируются два способа выполнения оценки с помощью R-модели в хранимой процедуре:

- **Режим оценки пакета**: использовать запрос SELECT в качестве входных данных для хранимой процедуры. Хранимая процедура возвращает таблицу наблюдений, соответствующую входным вариантам.

- **Режим индивидуальной оценки**. Передайте набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.

Сначала рассмотрим, как в целом выполняется оценка.

## <a name="basic-scoring"></a>Основные вычисления

Хранимая процедура _PredictTip_ иллюстрирует базовый синтаксис для заключения вызова прогноза в хранимую процедуру.

```SQL
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max)  
AS  
BEGIN  
  
  DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
  FROM nyc_taxi_models);  
  EXEC sp_execute_external_script @language = N'R',  
                                  @script = N'  
mod <- unserialize(as.raw(model));  
print(summary(mod))  
OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
          predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
str(OutputDataSet)  
print(OutputDataSet)  
',  
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2  
  WITH RESULT SETS ((Score float));  
  
END  
  
GO
```

- Инструкция SELECT получает сериализованную модель из базы данных и сохраняет ее в переменной R `mod` для дальнейшей обработки с помощью языка R.

- Для оценки новых случаев извлекаются из [!INCLUDE[tsql](../../includes/tsql-md.md)] запрос, указанный в `@inquery`, первый параметр хранимой процедуры. По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`. Этот кадр данных передается в функцию `rxPredict` на языке R, которая формирует оценки.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,            predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Так как кадр данных может содержать одну строку, один и тот же код можно использовать как для пакетной, так и для индивидуальной оценки.
  
-   Значение, возвращаемое `rxPredict` функция **float** , представляет вероятность того, что драйвер возвращает совет любой величине.

## <a name="batch-scoring"></a>Массовая оценка

Теперь рассмотрим, как производится пакетная оценка.

1.  Сначала получим набор входных данных меньшего размера, с которым будем далее работать. Этот запрос создает список первых 10 поездок с числом пассажиров и другими характеристиками, необходимыми для составления прогноза.
  
    ```SQL
    SELECT TOP 10 a.passenger_count AS passenger_count,
        a.trip_time_in_secs AS trip_time_in_secs, 
        a.trip_distance AS trip_distance, 
        a.dropoff_datetime AS dropoff_datetime, 
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    FROM
    (
        SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,
         dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a
    LEFT OUTERJOIN
    (
    SELECT medallion, hack_license, pickup_datetime
    FROM nyctaxi_sample
    TABLESAMPLE (70 percent) REPEATABLE (98052)
    )b
    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime  
    WHERE b.medallion IS NULL
    ```

    **Образец результатов**
    
    ```
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

    Этот запрос можно использовать в качестве входных данных для хранимой процедуры _PredictTipBatchMode_, в качестве части загрузки.

2. Внимательно просмотрите код хранимой процедуры _PredictTipBatchMode_ в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```SQL
    /****** Object:  StoredProcedure [dbo].[PredictTipBatchMode]  ******/
    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @inquery nvarchar(max)
    AS
    BEGIN
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model
      FROM nyc_taxi_models);
      EXEC sp_execute_external_script @language = N'R',
        @script = N'
          mod <- unserialize(as.raw(model));
          print(summary(mod))
          OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
          str(OutputDataSet)
          print(OutputDataSet)
        ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  Введите текст запроса в переменной и передайте его в качестве параметра в хранимую процедуру:

    ```SQL
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='
    select top 10 a.passenger_count as passenger_count,
        a.trip_time_in_secs as trip_time_in_secs,
        a.trip_distance as trip_distance,
        a.dropoff_datetime as dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance
    from
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
        from nyctaxi_sample
    )a  
    LEFT OUTER JOIN
    (
    SELECT medallion, hack_license, pickup_datetime
    FROM nyctaxi_sample  
    TABLESAMPLE (70 percent) REPEATABLE (98052)
    )b 
    ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime  
    WHERE b.medallion is null'

    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[PredictTip] @inquery = @query_string;
    ```
  
4. Хранимая процедура возвращает последовательность значений, представляющий прогноз для каждого десять приема-передачи данных. Однако top приема-передачи также являются одним пассажира приема-передачи с расстоянием относительно короткий маршрут, для которого драйвер вряд ли получить совет.
  

> [!TIP]
> 
> Вместо получения результатов типа "Есть чаевые" или "Нет чаевых" можно также получить оценку вероятности, а затем применить предложение WHERE к значениям столбца _Score_ , чтобы классифицировать оценки как "высокая вероятность чаевых" или "низкая вероятность чаевых", используя пороговое значение, например 0,5 или 0,7. Это действие отсутствует в хранимой процедуре, но его можно легко реализовать.

## <a name="single-row-scoring"></a>Оценки одной строки

Иногда требуется передать из приложения отдельные значения и получить один результат на их основе. Например, можно настроить лист Excel, веб-приложение или отчет служб Reporting Services так, чтобы они вызывали хранимую процедуру, передавая в нее входные значения, введенные или выбранные пользователями.

В этом разделе вы узнаете, как создать единичные прогнозы с помощью хранимой процедуры.

1. Изучите код хранимой процедуры _PredictTipSingleMode_, которая входит в состав скачанного пакета.
  
    ```SQL
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
      SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count,  
    @trip_distance,  
    @trip_time_in_secs,  
    @pickup_latitude,  
    @pickup_longitude,  
    @dropoff_latitude,  
    @dropoff_longitude)  
        '  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
    @input_data_1 = @inquery,  
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  
    @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float',  
    @model = @lmodel2,  
    @passenger_count =@passenger_count ,  
    @trip_distance=@trip_distance,  
    @trip_time_in_secs=@trip_time_in_secs,    
    @pickup_latitude=@pickup_latitude,  
    @pickup_longitude=@pickup_longitude,  
    @dropoff_latitude=@dropoff_latitude,  
    @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```
  
    - Эта хранимая процедура принимает в качестве входных данных несколько отдельных значений, таких как число пассажиров, расстояние поездки и т. д.
  
        При вызове хранимой процедуры из внешнего приложения данные должны соответствовать требованиям модели R. К ним могут относиться возможность приведения или преобразования входных данных в тип данных R или проверка типа и длины данных. Дополнительные сведения см. в разделе [Работа с типами данных R](https://msdn.microsoft.com/library/mt590948.aspx).
  
    -   Хранимая процедура создает оценку на основе сохраненной модели R.
  
2. Попробуйте выполнить ее, указав значения вручную.
  
    Откройте новый **запроса** окна, а вызов хранимой процедуры, предоставляя значений для каждого параметра. Параметры представляют столбцы компонентов, используемых в модели и являются обязательными.

    ```
    EXEC [dbo].[PredictTipSingleMode] @passenger_count = 0,
    @trip_distance float = 2.5,
    @trip_time_in_secs int = 631,
    @pickup_latitude float = 40.763958,
    @pickup_longitude float = -73.973373,
    @dropoff_latitude float =  40.782139,
    @dropoff_longitude float = 73.977303
    ```

    Также можно использовать этот короткий форме, которая поддерживается для [параметров для хранимой процедуры](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Результаты показывают, что вероятность получения совет не хватает эти top 10 приема-передачи, так как все являются одним пассажира приема-передачи данных через короткое расстояние.

## <a name="conclusions"></a>Заключение

На этом шаге работа с учебником завершается. Теперь, когда вы изучили встраивать код R в хранимые процедуры, можно расширить эти методы для построения моделей свой собственный. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] значительно упрощает развертывание моделей R для прогнозирования и включения переобучения моделей в корпоративные рабочие процессы по обработке данных.

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 5: Обучения и сохранить модель R с помощью T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)

