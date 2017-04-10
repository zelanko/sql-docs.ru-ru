---
title: "Шаг&#160;6. Ввод модели в эксплуатацию (учебник по дополнительным аналитическим функциям в базе данных) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 52b05828-11f5-4ce3-9010-59c213a674d1
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Шаг&#160;6. Ввод модели в эксплуатацию (учебник по дополнительным аналитическим функциям в базе данных)
В этом шаге вы научитесь *вводить модель в эксплуатацию* с помощью хранимой процедуры. Эта хранимая процедура может вызываться напрямую другими приложениями для создания прогнозов на основе новых наблюдений.  
  
В этом шаге вы освоите два способа вызова модели R из хранимой процедуры.  
  
-   **Режим пакетной оценки**. Используйте запрос SELECT, чтобы предоставить несколько строк данных. Хранимая процедура возвращает таблицу наблюдений, соответствующую входным вариантам.  
  
-   **Режим индивидуальной оценки**. Передайте набор отдельных значений параметров в качестве входных данных.  Хранимая процедура возвращает одну строку или значение.  
  
Сначала рассмотрим, как в целом выполняется оценка.  
  
## Базовый процесс оценки  
Хранимая процедура _PredictTip_ иллюстрирует базовый синтаксис для заключения вызова прогноза в хранимую процедуру.  
  
```  
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
  
-   Инструкция SELECT получает сериализованную модель из базы данных и сохраняет ее в переменной R `mod` для дальнейшей обработки с помощью языка R.  
  
-   Новые варианты для оценки получаются с помощью запроса [!INCLUDE[tsql](../../includes/tsql-md.md)], указанного в `@inquery` — первом параметре хранимой процедуры. По мере считывания данных запроса строки сохраняются в кадре данных по умолчанию `InputDataSet`. Этот кадр данных передается в функцию `rxPredict` на языке R, которая формирует оценки.  
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,            predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`  
  
    Так как кадр данных может содержать одну строку, один и тот же код можно использовать как для пакетной, так и для индивидуальной оценки.  
  
-   Значение, возвращаемое функцией `rxPredict`, имеет тип **float** и представляет вероятность получения чаевых (в любом размере).  
  
## Пакетная оценка с помощью запроса SELECT  
Теперь рассмотрим, как производится пакетная оценка.  
  
1.  Сначала получим набор входных данных меньшего размера, с которым будем далее работать.  
  
    ```  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
    (  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null  
    ```  
  
    Этот запрос создает список первых 10 поездок с числом пассажиров и другими характеристиками, необходимыми для составления прогноза.  
  
 **Результаты**  
  
*passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance*  
*1  283 0.7 2013-03-27 14:54:50.000   0.5427964547*  
*1  289 0.7 2013-02-24 12:55:29.000   0.3797099614*  
*1  214 0.7 2013-06-26 13:28:10.000   0.6970098661*  
*1  276 0.7 2013-06-27 06:53:04.000   0.4478814362*  
*1  282 0.7 2013-02-21 07:59:54.000   0.5340645749*  
*1  260 0.7 2013-03-27 15:40:49.000   0.5513900727*  
*1  230 0.7 2013-02-05 09:47:59.000   0.5161578519*  
*1  250 0.7 2013-05-08 14:35:51.000   0.5626440915*  
*1  280 0.7 2013-05-11 12:22:01.000   0.5598517959*  
*1  308 0.7 2013-04-10 08:06:00.000   0.4478814362*  
  
Этот запрос будет использоваться в качестве входных данных хранимой процедуры _PredictTipBatchMode_, которая входит в состав скачанного пакета.  
  
2.  Сначала изучите код хранимой процедуры _PredictTipBatchMode_ в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    ```  
    /****** Object:  StoredProcedure [dbo].[PredictTipBatchMode]  ******/  
    SET ANSI_NULLS ON  
    GO  
    SET QUOTED_IDENTIFIER ON  
    GO  
  
    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @inquery nvarchar(max)  
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
    ```  
  
3.  Для составления прогнозов вы укажете текст запроса в переменной и передадите ее в качестве параметра в хранимую процедуру с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] наподобие приведенной ниже.  
  
    ```  
    -- Specify input query  
  
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
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null'  
  
    -- Call stored procedure for scoring  
    EXEC [dbo].[PredictTip] @inquery = @query_string;  
  
    ```  
  
4.  Хранимая процедура возвращает ряд значений, представляющих прогнозы для каждой из поездок. Если снова посмотреть на входные значения, то можно увидеть, что все они представляют поездки с одним пассажиром на сравнительно небольшое расстояние. Вероятность получения чаевых за такие поездки крайне мала.  
  
    Вместо получения результатов типа "Есть чаевые" или "Нет чаевых" можно также получить оценку вероятности, а затем применить предложение WHERE к значениям столбца _Score_, чтобы классифицировать оценки как "высокая вероятность чаевых" или "низкая вероятность чаевых", используя пороговое значение, например 0,5 или 0,7. Это действие отсутствует в хранимой процедуре, но его можно легко реализовать.  
  
## Оценка отдельных строк  
Иногда требуется передать из приложения отдельные значения и получить один результат на их основе. Например, можно настроить лист Excel, веб-приложение или отчет служб Reporting Services так, чтобы они вызывали хранимую процедуру, передавая в нее входные значения, введенные или выбранные пользователями.  
  
В этом разделе вы узнаете, как создавать отдельные прогнозы с помощью хранимой процедуры.  
  
1.  Изучите код хранимой процедуры _PredictTipSingleMode_, которая входит в состав скачанного пакета.  
  
    ```  
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
  
    -   Эта хранимая процедура принимает в качестве входных данных несколько отдельных значений, таких как число пассажиров, расстояние поездки и т. д.  
  
        При вызове хранимой процедуры из внешнего приложения данные должны соответствовать требованиям модели R. К ним могут относиться возможность приведения или преобразования входных данных в тип данных R или проверка типа и длины данных. Дополнительные сведения см. в разделе [Работа с типами данных R](https://msdn.microsoft.com/library/mt590948.aspx).  
  
    -   Хранимая процедура создает оценку на основе сохраненной модели R.  
  
2.  Попробуйте выполнить ее, указав значения вручную.  
  
    Откройте новое окно **Запрос** и вызовите хранимую процедуру, введя параметры для каждого из столбцов характеристик.  
  
    ```  
  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303  
  
    ```  
  
    Значения для столбцов характеристик указываются в следующем порядке:  
  
    -   *trip_time_in_secs*  
    -   *pickup_latitude*  
    -   *pickup_longitude*  
    -   *dropoff_latitude*  
    -   *dropoff_longitude*  
  
3.  Результаты говорят о том, что вероятность получения чаевых за эти 10 поездок, которые являются поездками с одним пассажиром на сравнительно короткое расстояние, очень мала.  
  
## Заключение  
В этом учебнике вы узнали, как работать с кодом на языке R, внедренным в хранимые процедуры. Интеграция с [!INCLUDE[tsql](../../includes/tsql-md.md)] значительно упрощает развертывание моделей R для прогнозирования и включения переобучения моделей в корпоративные рабочие процессы по обработке данных.  
  
  
## Предыдущий шаг  
[Шаг 4. Создание характеристик данных с помощью T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## См. также:  
[Дополнительные аналитические функции в базе данных для разработчиков SQL (учебник)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Учебники по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
