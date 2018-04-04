---
title: Создание компонентов данных, с помощью R и SQL (Пошаговое руководство) | Документы Microsoft
ms.custom: ''
ms.date: 08/23/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: ecbdc28ac530dcee1ba9f5a3820d999ad4e0fcd9
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="create-data-features-using-r-and-sql-walkthrough"></a>Создание компонентов данных, с помощью R и SQL (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Проектирование данных — это важная составляющая машинного обучения. Данные часто требуют преобразования, прежде чем можно будет использовать для прогнозирующего моделирования. Если данные не имеют требуемых характеристик, их необходимо создать на основе существующих значений.

Для этой задачи моделирования вместо необработанных значений широты и долготы мест посадки и высадки желательно использовать значения расстояния в километрах между этими двумя местами. Чтобы создать эту функцию, вычислений прямой линейное расстояние между двумя точками, с помощью [Формула гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula).

На этом шаге мы сравнить две различные методы для создания компонентов на основе данных:

- С помощью пользовательской функции R
- С помощью пользовательской функции в T-SQL [!INCLUDE[tsql](../../includes/tsql-md.md)]

Предназначена для того, чтобы создать новую [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набор данных, который содержит исходные столбцы, а также новый числовых признаков *direct_distance*.

## <a name="featurization-using-r"></a>Featurization с помощью R

Язык R известен своими статистическими библиотеками с широкими и разнообразными возможностями, но вам все еще нужно создавать пользовательские преобразования данных.

Во-первых, приступим привыкшим пользователей R: получение данных на вашем ноутбуке, а затем запустите пользовательскую функцию R, *ComputeDist*, которая вычисляет линейную расстояние между двумя точками, заданные значения широты и долготы.

1. Помните, что объект источника данных, созданную ранее возвращает только первые 1000 строк. Итак, давайте определить запрос, который получает все данные.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Создание источника данных SQL Server с помощью запроса.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) можно выполнить запрос, состоящий из допустимый запрос SELECT, предоставленных в качестве аргумента для _sqlQuery_ параметр или имя объекта таблицы, как _таблицы_ параметр.
    
    - Если вы хотите образец данных из таблицы, необходимо использовать _SQL-запрос_ параметра, определить параметры выборки данных с помощью предложения TABLESAMPLE T-SQL, а также задать _rowBuffering_ аргумента значение FALSE.

3. Выполните следующий код, чтобы создать пользовательскую функцию R. ComputeDist отображаются две пары значений широты и долготы, а также вычисляет линейную расстояния между ними возвращает расстояние в милях.

    ```R
    env <- new.env();
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
  
    + В первой строке определяется новая среда. В R среду можно использовать для инкапсуляции пространств имен в пакетах и отдельно.  С помощью функции `search()` можно просмотреть среды, имеющиеся в рабочем пространстве. Чтобы просмотреть объекты в определенной среде, введите `ls(<envname>)`.
    + Строки начиная с `$env.ComputeDistance` содержат код, который определяет формулу гаверсинуса, вычисляющую *ортодромическое расстояние* между двумя точками на сфере.

4. После определения функции, можно применить его к данным, чтобы создать новый столбец признаков *direct_distance*. Однако перед запуском преобразования, изменить контекст вычислений к локальным.

    ```R
    rxSetComputeContext("local");
    ```

5. Вызовите [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) функции для функции, инженерных данных и применить `env$ComputeDist` функцию для данных в памяти.

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureEngineeringQuery,
    transforms = list(direct_distance=ComputeDist(pickup_longitude,pickup_latitude, dropoff_longitude, dropoff_latitude),
    tipped = "tipped", fare_amount = "fare_amount", passenger_count = "passenger_count",
    trip_time_in_secs = "trip_time_in_secs",  trip_distance="trip_distance",
    pickup_datetime = "pickup_datetime",  dropoff_datetime = "dropoff_datetime"),
    transformEnvir = env,
    rowsPerRead=500,
    reportProgress = 3);
  
    used.time <- proc.time() - start.time;
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""));
    ```

    + Функция rxDataStep поддерживает различные методы для изменения данных на месте. Дополнительные сведения см. в разделе этой статьи: [преобразования и подмножество данных в R произведите](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Однако моментов заметить относительно rxDataStep: 
    
    В других источниках данных, можно использовать аргументы *varsToKeep* и *varsToDrop*, но они не поддерживаются для источников данных SQL Server. Таким образом, в этом примере мы используем _преобразует_ для указания сквозные столбцы и столбцы преобразованный аргумент. Кроме того, когда работает в SQL Server контекста вычислений, _inData_ аргумент может принимать только из источника данных SQL Server.

    Приведенный выше код можно также создавать предупреждение при запуске на более крупных наборов данных. При истечении времени число строк, число столбцов создаваемого превышает заданное значение (значение по умолчанию — 3,000,000), rxDataStep возвращает предупреждение и количество строк в фрейме, возвращаемые данные будут усечены. Чтобы устранить это предупреждение, можно изменить _maxRowsByCols_ аргумент в функции rxDataStep. Однако если _maxRowsByCols_ слишком велик, могут возникнуть проблемы при загрузке кадров данных в памяти.

7. Кроме того, можно вызвать [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) для проверки схемы источника преобразованные данные.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Добавление признаков с помощью Transact-SQL

Теперь создайте пользовательскую функцию SQL, *ComputeDist*, для выполнения этой задачи пользовательскую функцию R.

1. Задайте новую пользовательскую функцию SQL с именем *fnCalculateDistance*. Код этой пользовательской функции SQL предоставлен в скрипте PowerShell, который вы выполняли для создания и настройки базы данных.  Функция уже должна существовать в вашей базе данных.

    Если она не существует, создайте функцию в той же базе данных, где хранятся данные по работе такси, используя SQL Server Management Studio.

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS
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

2. Чтобы увидеть только работу функции, выполните следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] из любого приложения, которое поддерживает [!INCLUDE[tsql](../../includes/tsql-md.md)].

    ```sql
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
    FROM nyctaxi_sample
    ```
3. После определения этой функции, могут быть легко создать с помощью SQL требуемые компоненты и затем вставить значения непосредственно в новую таблицу:

    ```
    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
    pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Тем не менее давайте посмотрим, как вызвать пользовательскую функцию SQL из кода R. Во-первых можно храните featurization SQL-запроса в переменную R.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Этот запрос был изменен для получения более мелкие образец данных, чтобы ускорить в данном пошаговом руководстве. Предложение TABLESAMPLE можно удалить, если требуется получить все данные; Тем не менее в зависимости от среды, не можно загрузить полный набором данных в R, что приводит к ошибке.
  
5. Используйте приведенные ниже строки кода, чтобы вызвать функцию [!INCLUDE[tsql](../../includes/tsql-md.md)] из среды R и применить ее к данным, определенным в *featureEngineeringQuery*.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
             dropoff_longitude = "numeric", dropoff_latitude = "numeric",
             passenger_count  = "numeric", trip_distance  = "numeric",
              trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Теперь, когда создается новая функция, вызовите **rxGetVarsInfo** Создание сводку данных в таблице feature.
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    *Результаты*

    ```
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: numeric
    Var 4: trip_time_in_secs, Type: numeric
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: direct_distance, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: pickup_longitude, Type: numeric
    Var 11: dropoff_latitude, Type: numeric
    Var 12: dropoff_longitude, Type: numeric
    ```

    > [!NOTE]
    > В некоторых случаях может появиться ошибка такого рода: *запрещено разрешение EXECUTE на объект «fnCalculateDistance»* в этом случае убедитесь, что используется имя входа имеет разрешения на выполнение сценариев и создания объектов в базе данных не только на экземпляре.
    > Проверка схемы для объекта fnCalculateDistance. Если объект был создан владелец базы данных и имя входа принадлежит роли db_datareader, нужно предоставить имя входа явные разрешения для выполнения скрипта.

## <a name="comparing-r-functions-and-sql-functions"></a>Сравнение функций R и функции SQL

Запоминать эту часть кода, использованной для код R времени?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

Попробуйте использовать это показано в примере пользовательская функция SQL, чтобы увидеть, как долго выполняет преобразование данных, при вызове функции SQL. Кроме того попробуйте переключиться контекстов вычислений с rxSetComputeContext и сравните затраты времени.

Ваш раз может сильно различаться, в зависимости от скорости сети и конфигурации оборудования. В конфигурациях, мы протестировали [!INCLUDE[tsql](../../includes/tsql-md.md)] функция подход был быстрее, чем с помощью пользовательской функции R. Таким образом, что мы познакомились с использование [!INCLUDE[tsql](../../includes/tsql-md.md)] функция эти вычисления в последующих шагах.

> [!TIP]
> Очень часто компонентов проектирование с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] будет выполняться быстрее, чем R. Например, T-SQL включает быстрого управления окнами и Ранжирующие функции, которые могут быть применены к общие вычисления обработки и анализа данных, например чередующихся скользящих средних и *n*-плитки. Выберите наиболее эффективный способ в зависимости от особенностей данных и поставленной задачи.

## <a name="next-lesson"></a>Следующее занятие

[Построить модель R и сохранить в SQL](walkthrough-build-and-save-the-model.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Просмотр и сведение данных с помощью R](walkthrough-view-and-summarize-data-using-r.md)

