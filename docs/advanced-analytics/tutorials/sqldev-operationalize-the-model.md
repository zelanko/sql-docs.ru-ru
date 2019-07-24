---
title: Занятие 4. прогнозирование возможных результатов с помощью моделей R
description: Руководство, в котором показано, как эксплуатацию внедренный скрипт R в SQL Server хранимых процедур с помощью функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 159fb29bf560e755fdc605330d7d20369f55ba08
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345895"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>Занятие 4: Выполнение прогнозов с помощью R Embedded в хранимой процедуре
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья является частью руководства для разработчиков SQL, посвященных использованию R в SQL Server.

На этом шаге вы научитесь использовать модель в отношении новых наблюдений для прогнозирования возможных результатов. Модель упаковывается в хранимую процедуру, которую можно вызывать непосредственно другими приложениями. В этом пошаговом руководстве демонстрируется несколько способов выполнения оценки:

- **Режим пакетной оценки**: Используйте запрос SELECT в качестве входных данных для хранимой процедуры. Хранимая процедура возвращает таблицу наблюдений, соответствующую входным вариантам.

- **Отдельный режим оценки**: Передайте набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.

Сначала рассмотрим, как в целом выполняется оценка.

## <a name="basic-scoring"></a>Базовая оценка

Хранимая процедура **RxPredict** иллюстрирует базовый синтаксис для упаковки вызова RevoScaleR RxPredict в хранимой процедуре.

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

+ Инструкция SELECT получает сериализованную модель из базы данных и сохраняет ее в переменной `mod` r для дальнейшей обработки с помощью языка r.

+ Новые варианты для оценки получаются из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса, указанного в `@inquery`, первый параметр хранимой процедуры. По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`. Этот кадр данных передается в функцию [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) в [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), которая создает оценки.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Так как кадр данных может содержать одну строку, один и тот же код можно использовать как для пакетной, так и для индивидуальной оценки.
  
+ Значение, возвращаемое `rxPredict` функцией, является числом с **плавающей запятой** , представляющим вероятность того, что драйвер получает Совет любой суммы.

## <a name="batch-scoring-a-list-of-predictions"></a>Пакетная Оценка (список прогнозов)

Более распространенный сценарий состоит в формировании прогнозов для нескольких наблюдений в пакетном режиме. На этом этапе давайте посмотрим, как работает Пакетная оценка.

1.  Начните с получения меньшего набора входных данных для работы. Этот запрос создает список первых 10 поездок с числом пассажиров и другими характеристиками, необходимыми для составления прогноза.
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Примеры результатов**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. Создайте хранимую процедуру с  именем ркспредиктбатчаутпут [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в.

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

3.  Укажите текст запроса в переменной и передайте его в хранимую процедуру в качестве параметра:

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
Хранимая процедура возвращает ряд значений, представляющих прогноз для каждого из 10 ведущих поездок. Тем не менее, самые популярные пути — это также однопассажировные поездки с относительно коротким расстоянием поездок, для которого драйвер вряд ли получает Совет.
  

> [!TIP]
> 
> Вместо того чтобы возвращать результаты "да-Совет" и "без TIP", можно также вернуть оценку вероятности для прогноза, а затем применить предложение WHERE к значениям столбца _оценки_ , чтобы классифицировать оценку как "вероятная подсказка" или "вряд ли для TIP", используя пороговое значение, например 0,5 или 0,7. Это действие отсутствует в хранимой процедуре, но его можно легко реализовать.

## <a name="single-row-scoring-of-multiple-inputs"></a>Однострочная оценка нескольких входов

Иногда требуется передать несколько входных значений и получить один прогноз на основе этих значений. Например, можно настроить лист Excel, веб-приложение или Reporting Services отчет, чтобы вызвать хранимую процедуру и предоставить входные или выбранные пользователем данные из этих приложений.

В этом разделе вы узнаете, как создавать отдельные прогнозы с помощью хранимой процедуры, которая принимает несколько входных данных, таких как количество пассажиров, расстояние поездок и т. д. Хранимая процедура создает оценку на основе ранее сохраненной модели R.
  
При вызове хранимой процедуры из внешнего приложения убедитесь, что данные соответствуют требованиям модели R. К ним могут относиться возможность приведения или преобразования входных данных в тип данных R или проверка типа и длины данных. 

1. Создайте хранимую процедуру **ркспредиктсинглеров**.
  
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
  
    Откройте новое окно **запроса** и вызовите хранимую процедуру, указав значения для каждого из параметров. Параметры представляют столбцы функций, используемые моделью, и являются обязательными.

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

    Или используйте более короткий формат, поддерживаемый для [параметров хранимой процедуры](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Результаты указывают на то, что вероятность получения Совета невелика (ноль) в этих 10 поездках, так как все это пассажировные поездки на относительно коротком расстоянии.

## <a name="conclusions"></a>Заключение

На этом шаге работа с учебником завершается. Теперь, когда вы узнали, как внедрять код R в хранимые процедуры, вы можете расширить эти методы для создания собственных моделей. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] значительно упрощает развертывание моделей R для прогнозирования и включения переобучения моделей в корпоративные рабочие процессы по обработке данных.

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 3. Обучение и сохранение модели R с помощью T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)
