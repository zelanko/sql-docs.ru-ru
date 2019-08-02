---
title: Создание функций данных с помощью функций R и SQL Server
description: Учебник, показывающий, как создавать функции данных с помощью функций SQL Server для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f12c20a54c0811e392eaa85684d7fac1a209c396
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714688"
---
# <a name="create-data-features-using-r-and-sql-server-walkthrough"></a>Создание функций данных с помощью R и SQL Server (пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Проектирование данных — это важная составляющая машинного обучения. Данные часто требуют преобразования, прежде чем их можно будет использовать для прогнозного моделирования. Если данные не имеют требуемых характеристик, их необходимо создать на основе существующих значений.

Для этой задачи моделирования вместо необработанных значений широты и долготы мест посадки и высадки желательно использовать значения расстояния в километрах между этими двумя местами. Чтобы создать эту функцию, необходимо вычислить прямое линейное расстояние между двумя точками с помощью [формулы Формула гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula).

На этом шаге вы узнаете о двух различных методах создания функции на основе данных:

> [!div class="checklist"]
> * Использование пользовательской функции R
> * Использование пользовательской функции T-SQL в[!INCLUDE[tsql](../../includes/tsql-md.md)]

Целью является создание нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набора данных, включающего в себя исходные столбцы и новую числовую функцию *direct_distance*.

## <a name="prerequisites"></a>предварительные требования

Этот шаг предполагает выполнение текущего сеанса R на основе предыдущих шагов этого пошагового руководства. В нем используются строки подключения и объекты источников данных, созданные в этих шагах. Для запуска скрипта используются следующие средства и пакеты.

+ RGUI. exe для выполнения команд R
+ Management Studio для выполнения T-SQL

## <a name="featurization-using-r"></a>Добавление признаков с помощью R

Язык R известен своими статистическими библиотеками с широкими и разнообразными возможностями, но вам все еще нужно создавать пользовательские преобразования данных.

Во-первых, давайте начнем с того, как пользователи R привыкли: получить данные на портативный компьютер, а затем выполнить пользовательскую функцию R *ComputeDist*, которая вычисляет линейное расстояние между двумя точками, заданными значениями широты и долготы.

1. Помните, что созданный ранее объект источника данных возвращает только первые 1000 строк. Итак, давайте определим запрос, который получает все данные.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Создайте новый объект источника данных с помощью запроса.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) может принимать либо запрос, состоящий из допустимого запроса SELECT, который указывается в качестве аргумента параметра _sqlQuery_ , либо имя объекта таблицы, предоставленное в качестве параметра _Table_ .
    
    - Если требуется образец данных из таблицы, необходимо использовать параметр _sqlQuery_ , определить параметры выборки с помощью предложения TABLESAMPLE T-SQL и присвоить аргументу _ровбуфферинг_ значение false.

3. Выполните следующий код, чтобы создать пользовательскую функцию R. ComputeDist принимает две пары значений широты и долготы и вычисляет линейное расстояние между ними, возвращая расстояние в милях.

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
  
    + В первой строке определяется новая среда. В R среду можно использовать для инкапсуляции пространств имен в пакетах и отдельно. С помощью функции `search()` можно просмотреть среды, имеющиеся в рабочем пространстве. Чтобы просмотреть объекты в определенной среде, введите `ls(<envname>)`.
    + Строки начиная с `$env.ComputeDist` содержат код, который определяет формулу гаверсинуса, вычисляющую *ортодромическое расстояние* между двумя точками на сфере.

4. Определив функцию, вы примените ее к данным для создания нового столбца функции *direct_distance*. но перед выполнением преобразования измените контекст вычислений на локальный.

    ```R
    rxSetComputeContext("local");
    ```

5. Вызовите функцию [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) для получения данных о проектировании компонентов и примените `env$ComputeDist` функцию к данным в памяти.

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureDataSource,
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

    + Функция rxDataStep поддерживает различные методы изменения данных на месте. Дополнительные сведения см. в этой статье:  [Преобразование и подсчета подмножества данных в Microsft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Однако стоит отметить несколько моментов, касающихся rxDataStep: 
    
    В других источниках данных можно использовать аргументы *varsToKeep* и *varsToDrop*, но они не поддерживаются для SQL Server источников данных. Таким образом, в этом примере мы использовали аргумент _TRANSFORMS_ для указания и передаваемых столбцов, и преобразованных столбцов. Кроме того, при выполнении в контексте вычислений SQL Server аргумент _undata_ может принимать только SQL Server источник данных.

    Приведенный выше код может также выдавать предупреждающее сообщение при выполнении в больших наборах данных. Если количество строк превышает число создаваемых столбцов, то в результате получается заданное значение (по умолчанию — 3 000 000), rxDataStep возвращает предупреждение, а число строк в возвращенном кадре данных будет обрезано. Чтобы устранить это предупреждение, можно изменить аргумент _максровсбиколс_ в функции rxDataStep. Однако если _максровсбиколс_ слишком большой, при загрузке кадра данных в память могут возникнуть проблемы.

7. При необходимости можно вызвать [функцию rxgetvarinfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) , чтобы проверить схему преобразованного источника данных.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Добавление признаков с помощью Transact-SQL

В этом упражнении вы узнаете, как выполнить ту же задачу с помощью функций SQL, а не пользовательских функций R. 

Чтобы запустить скрипт T-SQL, переключитесь на [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) или другой редактор запросов.

1. Используйте функцию SQL с именем *fnCalculateDistance*. Функция должна уже существовать в базе данных NYCTaxi_Sample. В обозревателе объектов убедитесь, что функция существует, перейдя по этому пути: Базы данных > Программирование > NYCTaxi_Sample > функции > скалярные функции > dbo. fnCalculateDistance.

    Если функция не существует, используйте SQL Server Management Studio, чтобы создать функцию в базе данных NYCTaxi_Sample.

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS decimal(28, 10)
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

2. В Management Studio в новом окне запроса выполните следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию из любого приложения, которое поддерживает [!INCLUDE[tsql](../../includes/tsql-md.md)] , чтобы увидеть, как работает функция.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude 
    FROM nyctaxi_sample
    ```
3. Чтобы вставить значения непосредственно в новую таблицу (сначала необходимо создать ее), можно добавить предложение **Into** , указав имя таблицы.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Можно также вызвать функцию SQL из кода R. Вернитесь в RGUI и сохраните запрос SQL Добавление признаков в переменной R.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Этот запрос был изменен для получения меньшего примера данных, чтобы ускорить выполнение этого пошагового руководства. Если требуется получить все данные, можно удалить предложение TABLESAMPLE. Однако в зависимости от среды загрузка полных датсет в R может оказаться невозможной, что приведет к ошибке.
  
5. Используйте приведенные ниже строки кода, чтобы вызвать функцию [!INCLUDE[tsql](../../includes/tsql-md.md)] из среды R и применить ее к данным, определенным в *featureEngineeringQuery*.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
        dropoff_longitude = "numeric", dropoff_latitude = "numeric",
        passenger_count  = "numeric", trip_distance  = "numeric",
        trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Теперь, когда новая функция создана, вызовите **рксжетварсинфо** , чтобы создать сводку по данным в таблице Feature.
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    **Результаты**

    ```R
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
    > В некоторых случаях может появиться сообщение об ошибке следующего вида: *Запрещено разрешение EXECUTE для объекта ' fnCalculateDistance '* Если это так, убедитесь, что используемое имя входа имеет разрешения на выполнение скриптов и создание объектов в базе данных, а не только на экземпляре.
    > Проверьте схему для объекта fnCalculateDistance. Если объект был создан владельцем базы данных, а имя входа принадлежит роли db_datareader, то для выполнения скрипта необходимо предоставить разрешения на явное имя входа.

## <a name="comparing-r-functions-and-sql-functions"></a>Сравнение функций R и функций SQL

Помните, что этот фрагмент кода используется для времени кода R?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

Можно попробовать использовать его с примером пользовательской функции SQL, чтобы узнать, как долго выполняется преобразование данных при вызове функции SQL. Кроме того, попробуйте переключить контексты вычислений с помощью rxSetComputeContext и сравнить временные показатели.

Время может значительно варьироваться в зависимости от скорости сети и конфигурации оборудования. В тестируемых конфигурациях подход к [!INCLUDE[tsql](../../includes/tsql-md.md)] функциям был быстрее, чем использование пользовательской функции R. Поэтому мы используем [!INCLUDE[tsql](../../includes/tsql-md.md)] функцию для этих вычислений в последующих шагах.

> [!TIP]
> Очень часто проектирование признаков [!INCLUDE[tsql](../../includes/tsql-md.md)] будет выполняться быстрее, чем на R. Например, T-SQL включает быстрые функции для работы с окнами и ранжирования, которые можно применять к общим вычислениям обработки и анализу данных, таким как скользящее среднее и *n*-плитки. Выберите наиболее эффективный способ в зависимости от особенностей данных и поставленной задачи.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание модели R и сохранение в SQL](walkthrough-build-and-save-the-model.md)

