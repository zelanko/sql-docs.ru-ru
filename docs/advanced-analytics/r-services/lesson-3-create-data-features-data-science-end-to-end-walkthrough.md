---
title: "Занятие&#160;3. Создание характеристик данных (пошаговое руководство по обработке и анализу данных) | Microsoft Docs"
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
ms.assetid: 4981d4eb-0874-4fe9-82e1-edf99890e27a
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Занятие&#160;3. Создание характеристик данных (пошаговое руководство по обработке и анализу данных)
Проектирование данных — еще одна важная составляющая машинного обучения. Прежде чем использовать данные для прогнозирующего моделирования, их зачастую требуется преобразовать. Если данные не имеют требуемых характеристик, их необходимо создать на основе существующих значений.  
  
Для этой задачи моделирования вместо необработанных значений широты и долготы мест посадки и высадки желательно использовать значения расстояния в километрах между этими двумя местами. Чтобы создать такую характеристику, необходимо вычислить прямое линейное расстояние между двумя местами по [формуле гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula).  
Вы сравните два разных способа создания характеристик на основе данных:  
  
-   с помощью языка R и функции `rxDataStep` ;    
-   с помощью пользовательской функции в [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
В обоих случаях результатом выполнения кода является объект источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `featureDataSource`, который содержит новую числовую характеристику `direct_distance`.  
  
## <a name="creating-features-using-r"></a>Создание характеристик с помощью языка R  

Язык R известен своими статистическими библиотеками с широкими и разнообразными возможностями, но вам все еще нужно создавать пользовательские преобразования данных. 

+ Вы создадите функцию R `ComputeDist` для вычисления линейного расстояния между двумя точками, которые заданы посредством широты и долготы.  
+ Вы вызовете функцию для преобразования данных в ранее созданном объекте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сохранения в новом источнике данных `featureDataSource`.  

### <a name="create-the-transformation-function"></a>Создание функции преобразования  
1.  Создайте пользовательскую функцию R `ComputeDist`. Она принимает две пары значений широты и долготы и вычисляет линейное расстояние между ними.  Функция возвращает расстояние в километрах.
  
    ```R  
    env <- new.env()  
    env$ComputeDist <- function(pickup_long, pickup_lat, dropoff_long, dropoff_lat){  
      R <- 6371/1.609344 #radius in mile  
      delta_lat <- dropoff_lat - pickup_lat  
      delta_long <- dropoff_long - pickup_long  
      degrees_to_radians = pi/180.0  
      a1 <- sin(delta_lat/2*degrees_to_radians)  
      a2 <- as.numeric(a1)^2  
      a3 <- cos(pickup_lat*degrees_to_radians)  
      a4 <- cos(dropoff_lat*degrees_to_radians)  
      a5 <- sin(delta_long/2*degrees_to_radians)  
      a6 <- as.numeric(a5)^2  
      a <- a2+a3*a4*a6  
      c <- 2*atan2(sqrt(a),sqrt(1-a))  
      d <- R*c  
      return (d)  
    }  
    ```  
  
    + В первой строке определяется новая среда. В R среду можно использовать для инкапсуляции пространств имен в пакетах и отдельно.
    + С помощью функции `search()` можно просмотреть среды, имеющиеся в рабочем пространстве. Чтобы просмотреть объекты в определенной среде, введите `ls(<envname>)`. 
    + Строки начиная с `$env.ComputeDistance` содержат код, который определяет формулу гаверсинуса, вычисляющую *ортодромическое расстояние* между двумя точками на сфере.  
 
  
### <a name="apply-the-transformation-function-to-data"></a>Применение функции преобразования к данным

Определив функцию, вы примените ее к данным, чтобы создать столбец характеристик *direct_distance*.

1. Создайте источник данных, который будет использоваться, с помощью конструктора `RxSqlServerData`.  
  
    ```R  
    featureDataSource = RxSqlServerData(table = "features",   
       colClasses = c(pickup_longitude = "numeric", 
       pickup_latitude = "numeric",   
       dropoff_longitude = "numeric", 
       dropoff_latitude = "numeric",  
       passenger_count  = "numeric", 
       trip_distance  = "numeric",  
       trip_time_in_secs  = "numeric", 
       direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
3.  Вызовите функцию `rxDataStep`, чтобы применить функцию `env$ComputeDist` к указанным данным.  
    
    ```R  
    start.time <- proc.time()  
  
    rxDataStep(inData = inDataSource, outFile = featureDataSource,  
         overwrite = TRUE,  
         varsToKeep=c("tipped", "fare_amount", passenger_count", "trip_time_in_secs", 
            "trip_distance", "pickup_datetime", "dropoff_datetime", "pickup_longitude",
            "pickup_latitude", "dropoff_longitude", "dropoff_latitude")
         , transforms = list(direct_distance=ComputeDist(pickup_longitude, 
            pickup_latitude, dropoff_longitude, dropoff_latitude)),
            transformEnvir = env, rowsPerRead=500, reportProgress = 3)  
  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```  
  
    + Функция `rxDataStep` может изменять данные на месте. Аргументы включают символьный вектор столбцов для передачи (*varsToKeep*) и список, определяющий преобразования.
    + Все преобразуемые столбцы выводятся автоматически, поэтому их не нужно включать в аргумент *varsToKeep* .
    + Кроме того, с помощью аргумента *varsToDrop* можно указать, что должны включаться все исходные столбцы, кроме указанных переменных.  
  
4.  Наконец, вызовите `rxGetVarInfo`, чтобы проверить схему для нового источника данных:  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
    *Результаты*
    
    *Затрачено времени ЦП — 0,74 с, затрачено времени — 35,75 с на создание характеристик*.  
    *Var 1: tipped, тип: integer*   
    *Var 2: fare_amount, тип: numeric*   
    *Var 3: passenger_count, тип: numeric*   
    *Var 4: trip_time_in_secs, тип: numeric*   
    *Var 5: trip_distance, тип: numeric*   
    *Var 6: pickup_datetime, тип: character*   
    *Var 7: dropoff_datetime, тип: character*   
    *Var 8: pickup_longitude, тип: numeric*   
    *Var 9: pickup_latitude, тип: numeric*   
    *Var 10: dropoff_longitude, тип: numeric*   
    *Var 11: dropoff_latitude, тип: numeric*   
    *Var 12: direct_distance, тип: numeric*   
  
## <a name="creating-features-using-transact-sql"></a>Создание характеристик с помощью языка Transact-SQL  
Теперь, когда вы узнали, как создавать характеристики с помощью функции R, вы создадите пользовательскую функцию SQL `ComputeDist` для выполнения этой же задачи. Функция SQL `ComputeDist` обрабатывает существующий объект данных `RxSqlServerData` для создания характеристики расстояния на основе имеющихся значений широты и долготы.  
  
Результаты преобразования сохраняются в объекте данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `featureDataSource`, так же как и при использовании языка R.  
  
Зачастую формирование характеристик с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняется быстрее, чем с помощью языка R. Выберите наиболее эффективный способ в зависимости от особенностей данных и поставленной задачи.  

### <a name="define-the-t-sql-custom-function"></a>Определение пользовательской функции T-SQL
  
1.  Определите новую функцию SQL `fnCalculateDistance`.  
  
    ```tsql  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END  
  
    ```  

    + Код этой *пользовательской функции* SQL предоставлен в скрипте PowerShell, который вы выполняли для создания и настройки базы данных.  Функция уже должна существовать в вашей базе данных.  Если она не существует, создайте функцию в той же базе данных, где хранятся данные по работе такси, используя SQL Server Management Studio.

2.  Чтобы увидеть работу функции, выполните следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] из любого приложения, которое поддерживает [!INCLUDE[tsql](../../includes/tsql-md.md)].   
  
    ```tsql  
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,       
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude   
    FROM nyctaxi_sample  
  
    ```  
### <a name="call-the-sql-function-from-r"></a>Вызов функции SQL из R

1. Сохраните инструкцию SQL, которая вызывает пользовательскую функцию в переменной R.  
  
    ```R  
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,  
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,  
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude  
        FROM nyctaxi_joined_1_percent  
        tablesample (1 percent) repeatable (98052)"    
    ```  
  
    > [!TIP] Этот запрос несколько отличается от запроса [!INCLUDE[tsql](../../includes/tsql-md.md)], который использовался ранее. Он был изменен для того, чтобы уменьшить выборку данных и ускорить работу с этим пошаговым руководством.  
  
4.  Теперь используйте приведенные ниже строки кода, чтобы вызвать функцию [!INCLUDE[tsql](../../includes/tsql-md.md)] из среды R и применить ее к данным, определенным в `featureEngineeringQuery`.  
  
    ```R  
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,  
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",           
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",  
             passenger_count  = "numeric", trip_distance  = "numeric",  
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),  
      connectionString = connStr)  
    ```  
  
5.  Теперь, когда новая функция создана, вызовите `rxGetVarsInfo`, чтобы получить сводку по таблице характеристик.  
  
    ```R  
    rxGetVarInfo(data = featureDataSource)  
    ```  
  
## <a name="comparing-r-functions-and-sql-functions"></a>Сравнение функций R с функциями SQL

Как показывает практика, с помощью функции [!INCLUDE[tsql](../../includes/tsql-md.md)] эта задача выполняется быстрее, чем с помощью пользовательской функции R. Поэтому на последующих этапах вы будете использовать функцию [!INCLUDE[tsql](../../includes/tsql-md.md)] для этих вычислений.  

Перейдите к следующему занятию, чтобы узнать, как создать модель прогнозирования на основе данных и сохранить ее в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 4. Создание и сохранение модели (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Предыдущее занятие  
[Занятие 2. Просмотр и изучение данных (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
