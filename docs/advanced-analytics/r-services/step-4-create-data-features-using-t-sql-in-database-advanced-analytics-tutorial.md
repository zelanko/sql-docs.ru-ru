---
title: "Шаг&#160;4. Создание характеристик данных с помощью T-SQL (учебник по дополнительным аналитическим функциям в базе данных) | Microsoft Docs"
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
ms.assetid: 5b2f4c44-6192-40df-abf1-fc983844f1d0
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Шаг&#160;4. Создание характеристик данных с помощью T-SQL (учебник по дополнительным аналитическим функциям в базе данных)
После нескольких циклов исследования данных вы собрали определенной объем аналитической информации и готовы переходить к *формированию характеристик*. Процесс создания характеристик на основе необработанных данных — важнейший этап расширенного аналитического моделирования.  
  
На этом этапе вы научитесь создавать характеристики на основе необработанных данных с помощью функции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.  
  
## Определение функции  
Значения расстояний, которые содержатся в исходных данных, основаны на показаниях счетчиков и необязательно отражают расстояние по карте или фактическое расстояние поездки. Поэтому необходимо вычислить прямое расстояние между местами посадки и высадки с помощью координат, доступных в исходном наборе данных по работе такси в Нью-Йорке. Это можно сделать с помощью [формулы гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula) в пользовательской функции [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
Вы используете пользовательскую функцию T-SQL _fnCalculateDistance_ для вычисления расстояния по формуле гаверсинуса, а затем другую пользовательскую функцию T-SQL _fnEngineerFeatures_ для создания таблицы, содержащей все характеристики.  
  
#### Вычисление расстояния поездки с помощью функции fnCalculateDistance  
  
1.  Функция _fnCalculateDistance_ должна была быть загружена и зарегистрирована в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в рамках подготовки к работе с этим пошаговым руководством. Вкратце изучите код.  
  
    В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] последовательно разверните узлы **Программируемость**, **Функции** и **Скалярные функции**.   
    Щелкните правой кнопкой мыши функцию _fnCalculateDistance_, а затем выберите команду **Изменить**, чтобы открыть скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в новом окне запроса.  
  
    ```  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
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
    GO  
  
    ```  
  
    -   Функция является скалярной и возвращает одно значение предопределенного типа.  
  
    -   Она принимает в качестве входных значений широту и долготу мест посадки и высадки. Формула гаверсинуса преобразует координаты в радианы и использует полученные значения для вычисления прямого расстояния в километрах между этими двумя местами.  
  
Для добавления вычисленного значения в таблицу, которую можно использовать для обучения модели, применяется другая функция: _fnEngineerFeatures_.  
  
#### Сохранение характеристик с помощью функции _fnEngineerFeatures_  
  
1.  Изучите код пользовательской функции T-SQL _fnEngineerFeatures_, которая должна была быть создана для вас в рамках подготовки к работе с этим пошаговым руководством.  
  
    Это табличная функция, которая принимает несколько столбцов в качестве входных значений и выводит таблицу с несколькими столбцами характеристик.  Назначение этой функции — создать набор характеристик, который будет использоваться при построении модели. Функция _fnEngineerFeatures_ вызывает ранее созданную функцию T-SQL _fnCalculateDistance_ для получения прямого расстояния между местами посадки и высадки.  
  
    ```  
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS  
      RETURN  
      (  
      -- Add the SELECT statement with parameter references here  
      SELECT  
        @passenger_count AS passenger_count,  
        @trip_distance AS trip_distance,  
        @trip_time_in_secs AS trip_time_in_secs,  
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance  
  
      )  
    GO  
  
    ```  
  
2.  Чтобы убедиться в том, что эта функция работает, можно с ее помощью вычислить географическое расстояние поездок, для которых расстояние по счетчику было равно 0, но места посадки и высадки были разными.  
  
    ```  
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,  
        trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance  
        FROM nyctaxi_sample  
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0  
        ORDER BY trip_time_in_secs DESC  
    ```  
  
    Как видите, расстояние по счетчику не всегда соответствует географическому расстоянию. Вот почему формирование характеристик имеет такое важное значение.  
  
В следующем шаге вы научитесь использовать характеристики данных для обучения модели машинного обучения с помощью языка R.  
  
## Следующий шаг  
[Шаг 5. Обучение и сохранение модели с помощью T-SQL](../../advanced-analytics/r-services/step-5-train-and-save-a-model-using-t-sql.md)  
  
## Предыдущий шаг  
[Шаг 3. Анализ и визуализация данных](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)  
  
## См. также:  
[Дополнительные аналитические функции в базе данных для разработчиков SQL (учебник)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Учебники по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
