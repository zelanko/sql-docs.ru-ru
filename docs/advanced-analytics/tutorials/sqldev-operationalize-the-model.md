---
title: Занятие 4 Predict возможных выхода с помощью модели R - машинного обучения SQL Server
description: Руководство, описывающее для ввода в эксплуатацию встроенный скрипт R в SQL Server хранимые процедуры с помощью функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4e74f587177c31f55c952eb06ccb8a7e8960c93a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511591"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>Урок 4. Запустите прогнозы с помощью R, внедренный в хранимой процедуре
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит руководства для разработчиков SQL по использованию R в SQL Server.

На этом шаге вы узнаете, как использовать модель по новых наблюдений для предсказания возможных выхода. Модели заключается в хранимую процедуру, которая может вызываться напрямую другими приложениями. В примере демонстрируются несколько способов выполнять оценку:

- **Режим пакетной оценки**: Используйте запрос SELECT в качестве входных данных хранимой процедуры. Хранимая процедура возвращает таблицу наблюдений, соответствующую входным вариантам.

- **Режим индивидуальной оценки**: Передайте набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.

Сначала рассмотрим, как в целом выполняется оценка.

## <a name="basic-scoring"></a>Базовый процесс оценки

Хранимая процедура **RxPredict** иллюстрирует базовый синтаксис для заключения вызова rxPredict RevoScaleR в хранимой процедуре.

```sql
CREATE PROCEDURE [dbo].[RxPredict] (@model varchar(250), @inquery nvarchar(max))
AS 
BEGIN 

DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);  
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
GO
```

+ Инструкция SELECT получает сериализованную модель из базы данных и сохраняет ее в переменной R `mod` для дальнейшей обработки с помощью языка R.

+ Новые варианты для оценки получаются из [!INCLUDE[tsql](../../includes/tsql-md.md)] запрос, указанный в `@inquery`, первый параметр для хранимой процедуры. По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`. Этот кадр данных передается [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) работать в [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), которая формирует оценки.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Так как кадр данных может содержать одну строку, один и тот же код можно использовать как для пакетной, так и для индивидуальной оценки.
  
+ Значение, возвращенное `rxPredict` функция **float** , представляет вероятность того, что драйвер возвращает tip, любом размере.

## <a name="batch-scoring-a-list-of-predictions"></a>Пакетной оценки (список прогнозов)

Распространенный сценарий — для формирования прогнозов для нескольких наблюдений в пакетном режиме. На этом шаге давайте посмотрим, как производится пакетная оценка.

1.  Начинайте с получения меньший набор входных данных для работы с. Этот запрос создает список первых 10 поездок с числом пассажиров и другими характеристиками, необходимыми для составления прогноза.
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Пример результатов**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. Создайте хранимую процедуру с именем **RxPredictBatchOutput** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```sql
    CREATE PROCEDURE [dbo].[RxPredictBatchOutput] (@model varchar(250), @inquery nvarchar(max))
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script 
      @language = N'R',
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

3.  Укажите текст запроса в переменную и передать его в качестве параметра в хранимую процедуру:

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
Хранимая процедура возвращает ряд значений, представляющих прогнозы для каждой из первых 10 поездок. Тем не менее верхнем поездок, также являются одним пассажиром с расстоянием поездки в относительно короткий, для которого драйвер вряд ли чаевые.
  

> [!TIP]
> 
> Вместо того чтобы возвращать только «Да совет» и «нет чаевых» результаты, можно также получить оценку вероятности прогноза и затем применить предложение WHERE для _Оценка_ значения столбца, чтобы классифицировать оценки как «высокая вероятность чаевых» или " Низкая вероятность чаевых», используя пороговое значение, например 0,5 или 0,7. Это действие отсутствует в хранимой процедуре, но его можно легко реализовать.

## <a name="single-row-scoring-of-multiple-inputs"></a>Оценка одной строки из нескольких наборов входных данных

Иногда требуется передать несколько входных значений и получить один прогноз на основании этих значений. Например можно настроить лист Excel, веб-приложения или отчета служб Reporting Services для вызова хранимой процедуры и передачи входных данных введенные или выбранные пользователями из этих приложений.

В этом разделе вы узнаете, как создавать отдельные прогнозы с помощью хранимой процедуры, которая принимает несколько входов, например число пассажиров, расстояние поездки и т. д. Хранимая процедура создает оценку на основе ранее сохраненные модели R.
  
Если вызвать хранимую процедуру из внешнего приложения, убедитесь, что данные соответствуют требованиям модели r. К ним могут относиться возможность приведения или преобразования входных данных в тип данных R или проверка типа и длины данных. 

1. Создание хранимой процедуры **RxPredictSingleRow**.
  
    ```sql
    CREATE PROCEDURE [dbo].[RxPredictSingleRow] @model varchar(50), @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```

2. Попробуйте выполнить ее, указав значения вручную.
  
    Откройте новую **запроса** окно и вызовите хранимую процедуру, предоставляя значения для каждого из параметров. Параметры представляют столбцы признаков, используемых моделью и являются обязательными.

    ```sql
    EXEC [dbo].[RxPredictSingleRow] @model = 'RxTrainLogit_model',
    @passenger_count = 1,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = -73.977303
    ```

    Также можно использовать этот короткую форму, поддерживаемые для [параметров для хранимой процедуры](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Результаты показывают, что вероятность получения чаевых не хватает (ноль) в этих первых 10 поездок, так как все являются одним пассажиром на сравнительно короткое расстояние.

## <a name="conclusions"></a>Заключение

На этом шаге работа с учебником завершается. Теперь, когда было продемонстрировано, как встраивать код R в хранимые процедуры, вы можете расширить эти методы для построения моделей своим собственным. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] значительно упрощает развертывание моделей R для прогнозирования и включения переобучения моделей в корпоративные рабочие процессы по обработке данных.

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 3. Обучение и сохранение модели R с помощью T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)
