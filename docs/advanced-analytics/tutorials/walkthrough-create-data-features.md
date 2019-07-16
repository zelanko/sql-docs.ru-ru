---
title: Создание функций данных с помощью функции R и SQL Server — машинного обучения SQL Server
description: Учебник, в котором показано, как создание функций данных с помощью функции SQL Server для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5a17eb0c39e45080de83e39d002d8f6693131688
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961797"
---
# <a name="create-data-features-using-r-and-sql-server-walkthrough"></a>Создание функций данных с помощью R и SQL Server (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Проектирование данных — это важная составляющая машинного обучения. Данные часто требуется преобразование, прежде чем можно будет использовать для прогнозирующего моделирования. Если данные не имеют требуемых характеристик, их необходимо создать на основе существующих значений.

Для этой задачи моделирования вместо необработанных значений широты и долготы мест посадки и высадки желательно использовать значения расстояния в километрах между этими двумя местами. Чтобы создать эту функцию, вычислить прямое линейное расстояние между двумя точками, с помощью [Формула гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula).

На этом шаге дополнительные два метода создания характеристик на основе данных:

> [!div class="checklist"]
> * С помощью пользовательской функции R
> * С помощью пользовательской функции T-SQL в [!INCLUDE[tsql](../../includes/tsql-md.md)]

Целью является создание нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набор данных, который включает исходные столбцы, а также новый числовой признак, *direct_distance*.

## <a name="prerequisites"></a>предварительные требования

Этот шаг предполагает выполняющимся R сеансом, в зависимости от предыдущего шага в этом пошаговом руководстве. Он использует соединение строк и данных источника объекты, созданные в этих шагах. Для запуска сценария используются следующие средства и пакеты.

+ RGUI.exe для выполнения команд R
+ Management Studio для выполнения T-SQL

## <a name="featurization-using-r"></a>Добавление признаков с помощью R

Язык R известен своими статистическими библиотеками с широкими и разнообразными возможностями, но вам все еще нужно создавать пользовательские преобразования данных.

Во-первых, давайте сделаем его привыкли пользователей R: данные на ноутбуке, а затем запустите пользовательской функции R, *ComputeDist*, которая вычисляет линейное расстояние между двумя точками, которые заданы посредством широты и долготы.

1. Помните, что объект источника данных, созданную ранее возвращает только первые 1000 строк. Так что давайте определим запрос, который получает все данные.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Создайте объект источника данных с помощью запроса.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) можно выполнить запрос, состоящий из допустимого запроса SELECT, предоставленный в качестве аргумента для _sqlQuery_ параметр или имя объекта таблицы, как _таблицы_ параметр.
    
    - Если вы хотите демонстрационные данные из таблицы, необходимо использовать _sqlQuery_ параметра, определение параметров выборки с помощью предложения TABLESAMPLE T-SQL и настройка _rowBuffering_ аргумента значение false.

3. Выполните следующий код для создания пользовательской функции R. ComputeDist принимает две пары значений широты и долготы и вычисляет линейное расстояние между ними, возвращая расстояние в милях.

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

4. Определив функцию, можно применить ее к данным, чтобы создать столбец характеристик, *direct_distance*. но прежде чем выполнять преобразование, меняет контекст вычисления для локальных.

    ```R
    rxSetComputeContext("local");
    ```

5. Вызовите [rxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) функцию для получения данных конструирования признаков и применить `env$ComputeDist` функцию данных в памяти.

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

    + Функции rxDataStep поддерживает различные методы для изменения данных на месте. Дополнительные сведения см. в статье:  [Преобразование и набор данных в Microsft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Тем не менее несколько точек следует отметить в отношении rxDataStep: 
    
    В других источниках данных, можно использовать аргументы *varsToKeep* и *varsToDrop*, но они не поддерживаются для источников данных SQL Server. Таким образом, мы использовали в этом примере _преобразует_ аргумент, чтобы указать сквозные столбцы и преобразованными столбцами. Кроме того, когда работает в SQL Server контекст вычислений, _inData_ аргумент может принимать только источник данных SQL Server.

    Приведенный выше код также позволяет создавать предупреждение при запуске на более крупных наборов данных. Число строк времени число столбцов создаваемой превышает заданное значение (по умолчанию — 3,000,000), rxDataStep возвращает предупреждение и количество строк в кадре возвращаемые данные будут усечены. Чтобы устранить это предупреждение, можно изменить _maxRowsByCols_ аргумент в функции rxDataStep. Тем не менее если _maxRowsByCols_ слишком велик, могут возникнуть проблемы при загрузке кадр данных в памяти.

7. При необходимости можно вызвать [rxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) для проверки схемы источника преобразованные данные.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Добавление признаков с помощью Transact-SQL

В этом упражнении вы научитесь выполнения той же задачи, с помощью функций SQL вместо пользовательских функций R. 

Переключиться в режим [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) или другого редактора запросов, чтобы запустить сценарий T-SQL.

1. С помощью функции SQL с именем *fnCalculateDistance*. Функция должна уже существовать в базе данных NYCTaxi_Sample. В обозревателе объектов убедитесь, что функция существует, перейдя по этому пути: Базы данных > NYCTaxi_Sample > программирования > функции > скалярные функции > dbo.fnCalculateDistance.

    Если функция не существует, используйте SQL Server Management Studio, создайте функцию в базе данных NYCTaxi_Sample.

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

2. В среде Management Studio в новом окне запроса выполните следующую команду, [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции из любого приложения, который поддерживает [!INCLUDE[tsql](../../includes/tsql-md.md)] чтобы увидеть, как работает функция.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude 
    FROM nyctaxi_sample
    ```
3. Чтобы вставить значения непосредственно в таблицу (необходимо сначала создать), можно добавить **INTO** предложение, указав имя таблицы.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Можно также вызвать функцию SQL из кода R. Вернитесь в Rgui и хранить в переменной r. Добавление признаков SQL-запроса.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Этот запрос был изменен, чтобы уменьшить выборку данных, чтобы быстрее принимать в этом пошаговом руководстве. Предложение TABLESAMPLE можно удалить, если вы хотите получить все данные; Тем не менее в зависимости от среды, не возможно для загрузки полного набора данных в R, что приводит к ошибке.
  
5. Используйте приведенные ниже строки кода, чтобы вызвать функцию [!INCLUDE[tsql](../../includes/tsql-md.md)] из среды R и применить ее к данным, определенным в *featureEngineeringQuery*.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
        dropoff_longitude = "numeric", dropoff_latitude = "numeric",
        passenger_count  = "numeric", trip_distance  = "numeric",
        trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Теперь, когда создается новая функция, вызовите **rxGetVarsInfo** для создания сводки по данным в таблице feature.
  
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
    > В некоторых случаях может возникнуть ошибка следующего вида: *Запрещено разрешение EXECUTE на объекте «fnCalculateDistance»* Если это так, убедитесь, что вы используете имя входа имеет разрешения на запуск сценариев и создания объектов в базе данных, не только на экземпляре.
    > Проверьте схему для объекта, fnCalculateDistance. Если объект был создан владелец базы данных, а имя входа принадлежит роли db_datareader, необходимо предоставить имя входа явные разрешения для выполнения скрипта.

## <a name="comparing-r-functions-and-sql-functions"></a>Сравнение функций R с функциями SQL

Помните, этот фрагмент кода, используемый для раз код R?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

Попробуйте использовать это в примере пользовательская функция SQL, чтобы увидеть, как долго выполняет преобразование данных, при вызове функции SQL. Кроме того попробуйте переключиться контекстов вычислений с rxSetComputeContext и сравните затраты времени.

Ваши время может существенно зависит от скорости сети и конфигурации оборудования. В конфигурациях, мы протестировали [!INCLUDE[tsql](../../includes/tsql-md.md)] функция подход был быстрее, чем с помощью пользовательской функции R. Таким образом, мы включили [!INCLUDE[tsql](../../includes/tsql-md.md)] функция для этих вычислений в последующих шагах.

> [!TIP]
> Зачастую формирование признаков с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] будет быстрее, чем R. Например, T-SQL включает в себя быстрое Управление окнами и Ранжирующие функции, которые могут применяться для общих вычислений обработки и анализа данных, например вычисление скользящих средних и *n*-плитки. Выберите наиболее эффективный способ в зависимости от особенностей данных и поставленной задачи.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание модели R и сохранение to SQL](walkthrough-build-and-save-the-model.md)

