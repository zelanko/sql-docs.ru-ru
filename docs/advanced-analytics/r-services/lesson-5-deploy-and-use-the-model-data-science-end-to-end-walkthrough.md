---
title: "Занятие&#160;5. Развертывание и использование модели (пошаговое руководство по обработке и анализу данных) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
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
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Занятие&#160;5. Развертывание и использование модели (пошаговое руководство по обработке и анализу данных)
На этом занятии вы будете использовать модели R в рабочей среде, заключив хранимую в базе данных модель в хранимую процедуру. После этого можно вызывать хранимую процедуру из R или любого прикладного языка программирования, поддерживающего [!INCLUDE[tsql](../../includes/tsql-md.md)] (например, C#, Java, Python и т. д.), чтобы с помощью модели составлять прогнозы на основе новых наблюдений.  
  
Существует два разных способа вызова модели для оценки.  
  
-   **Режим массовой оценки** позволяет создавать несколько прогнозов на основе входных данных, полученных из запроса SELECT.  
  
-   **Режим индивидуальной оценки** позволяет создавать прогнозы по одному, передавая набор значений характеристик для конкретного случая в хранимую процедуру, которая возвращает отдельный прогноз или другое значение в качестве результата.  
  
Вы научитесь создавать прогнозы как с помощью метода индивидуальной оценки, так и с помощью метода массовой оценки.  
  
## <a name="batch-scoring"></a>Пакетная оценка  
Для удобства можно использовать хранимую процедуру, которая была создана при первом выполнении скрипта PowerShell на занятии 1. Эта хранимая процедура выполняет следующее:  
  
-   получает набор входных данных в виде запроса SQL;    
-   вызывает обученную модель логистической регрессии, которая была сохранена на предыдущем занятии;    
-   прогнозирует вероятность того, что водитель получит чаевые.  
  
### <a name="use-the-stored-procedure-predicttipbatchmode"></a>Использование хранимой процедуры PredictTipBatchMode

1. Вкратце изучите скрипт, определяющий хранимую процедуру *PredictTipBatchMode*. Он иллюстрирует несколько аспектов ввода модели в эксплуатацию с помощью служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
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

    + Обратите внимание на инструкцию SELECT, которая вызывает хранимую модель. Любую модель обучения можно хранить в таблице SQL с помощью столбца типа **varbinary(max)**. В этом коде модель извлекается из таблицы, сохраняется в переменной SQL _@lmodel2_ и передается в качестве параметра *mod* в системную хранимую процедуру [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
    + Входные данные, используемые для оценки, передаются в хранимую процедуру в виде строки.  
  
        Чтобы определить входные данные для данной модели, создайте запрос, возвращающий нужные данные. Данные, возвращаемые из базы данных, сохраняются в кадре данных *InputDataSet*. Все строки этого кадра данных используются для массовой оценки.
        + *InputDataSet* — это имя по умолчанию для входных данных процедуры [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). При необходимости можно определить другое имя переменной.
        + Для формирования оценок хранимая процедура вызывает функцию *rxPredict* из библиотеки **RevoScaleR**.
    + Возвращаемое значение хранимой процедуры ( *Score*) представляет собой прогнозируемую вероятность получения чаевых водителем.  
  
2.  При необходимости можно легко применить определенный фильтр к возвращаемым значениям, чтобы разделить их на категории "есть чаевые" или "без чаевых".  Например, вероятность менее 0,5 означает вероятное отсутствие чаевых.  
  
3.  Вызовите хранимую процедуру в пакетном режиме:  
  
    ```R  
    input = "N' 
      SELECT TOP 10 
          a.passenger_count AS passenger_count,   
          a.trip_time_in_secs AS trip_time_in_secs,  
          a.trip_distance AS trip_distance,  
          a.dropoff_datetime AS dropoff_datetime,    
          dbo.fnCalculateDistance(
            pickup_latitude, 
            pickup_longitude, 
            dropoff_latitude,
            dropoff_longitude) AS direct_distance   
      FROM  
      
      (SELECT medallion, hack_license, pickup_datetime,   
      passenger_count,trip_time_in_secs,trip_distance,    
      dropoff_datetime, pickup_latitude, pickup_longitude,   
      dropoff_latitude, dropoff_longitude from nyctaxi_sample)a  
      
      LEFT OUTER JOIN  
 
      ( SELECT medallion, hack_license, pickup_datetime 
        FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b  

      ON a.medallion=b.medallion 
        AND a.hack_license=b.hack_license 
        AND a.pickup_datetime=b.pickup_datetime  

      WHERE b.medallion is null  
    '"  
    q<-paste("EXEC PredictTipBatchMode @inquery = ", input, sep="")  
    sqlQuery (conn, q)  
  
    ```  
  
## <a name="single-row-scoring"></a>Оценка одной строки  

Вместо использования запроса для передачи входных значений в сохраненную модель R может потребоваться указать характеристики в качестве аргументов хранимой процедуры.  

### <a name="use-the-stored-procedure-predicttipsinglemode"></a>Использование хранимой процедуры PredictTipSingleMode
1.  Бегло просмотрите следующий код для хранимой процедуры *PredictTipSingleMode*, которая должна быть создана в базе данных.  
  
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
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, 
            @trip_distance,  
            @trip_time_in_secs,  
            @pickup_latitude,  
            @pickup_longitude,  
            @dropoff_latitude,  
            @dropoff_longitude)  
        '  
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
      @params = N'@model varbinary(max),
                @passenger_count int,
                @trip_distance float,
                @trip_time_in_secs int ,  
                @pickup_latitude float ,
                @pickup_longitude float ,
                @dropoff_latitude float ,
                @dropoff_longitude float',  
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
  
    Эта хранимая процедура принимает в качестве входных данных значения характеристик, например число пассажиров и расстояние поездки, оценивает эти характеристики с помощью хранимой модели R и выводит результат оценки.  
  
### <a name="call-the-stored-procedure-and-pass-parameters"></a>Вызов хранимой процедуры и передача параметров

1. В SQL Server Management Studio можно использовать инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** для вызова хранимой процедуры и передачи ей необходимых входных данных. .  
    ```tsql  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303   
    ```  
  
    Здесь передаются значения для переменных _passenger_count_, _trip_distance_, _trip_time_in_secs_, _pickup_latitude_, _pickup_longitude_, _dropoff_latitude_и _dropoff_longitude_соответственно.  
  
2.  Чтобы выполнить этот же вызов из кода R, просто определите переменную R, содержащую весь вызов хранимой процедуры. 
  
    ```R  
    q = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 "  
    ```  
  
    Здесь передаются значения для переменных _passenger_count_, _trip_distance_, _trip_time_in_secs_, _pickup_latitude_, _pickup_longitude_, _dropoff_latitude_и _dropoff_longitude_соответственно.  
  
### <a name="generate-scores"></a>Создание оценок

1. Вызовите функцию *sqlQuery* из пакета **RODBC** и передайте строку подключения и строковую переменную, содержащую вызов хранимой процедуры.  
  
    ```R  
    # predict with stored procedure in single mode  
    sqlQuery (conn, q)   
    ```  
  
    Дополнительные сведения о **RODBC** см. на странице [http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery](http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery).  
  
## <a name="conclusion"></a>Заключение  
Теперь, когда вы узнали, как работать с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сохранять модели обучения R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы сравнительно легко сможете создать дополнительные модели на основе этого набора данных. Например, вы можете попробовать создать следующие модели:  
  
-   модель регрессии, прогнозирующая размер чаевых;    
-   модель многоклассовой классификации, прогнозирующая, будет ли размер чаевых большим, средним или небольшим.  

Мы также рекомендуем просмотреть некоторые из представленных дополнительных примеров и ресурсов: 
+ [Сценарии и шаблоны решений для обработки и анализа данных](../../advanced-analytics/r-services/data-science-scenarios-and-solution-templates.md)
+ [Дополнительные аналитические функции в базе данных для разработчиков SQL (руководство)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)
+ [Microsoft R - Diving into Data Analysis](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r) (Знакомство с анализом данных в Microsoft R)
+ [Дополнительные ресурсы](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)
## <a name="previous-lesson"></a>Предыдущее занятие  
[Занятие 4. Создание и сохранение модели (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>См. также  
[Руководства по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
