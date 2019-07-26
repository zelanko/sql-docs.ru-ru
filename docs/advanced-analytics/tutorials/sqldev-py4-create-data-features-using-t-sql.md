---
title: Создание функций данных с помощью функций T-SQL и Python
description: Руководство, в котором показано, как добавлять вычисления в хранимые процедуры для использования в моделях машинного обучения Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f1e07ffa4423ccfc2cc0082910a2ca8aff8fd087
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468673"
---
# <a name="create-data-features-using-t-sql"></a>Создание функций данных с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

После исследования данных вы собрали некоторые аналитические данные из данных и готовы перейти к *проектированию функций*. Этот процесс создания функций из необработанных данных может быть важным шагом в расширенном моделировании аналитики.

Эта статья является частью руководства, [в базе данных Python Analytics для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом этапе вы научитесь создавать характеристики на основе необработанных данных с помощью функции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

## <a name="define-the-function"></a>Определение функции

Значения расстояний, которые содержатся в исходных данных, основаны на показаниях счетчиков и необязательно отражают расстояние по карте или фактическое расстояние поездки. Поэтому необходимо вычислить прямое расстояние между местами посадки и высадки с помощью координат, доступных в исходном наборе данных по работе такси в Нью-Йорке. Это можно сделать с помощью [формулы гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula) в пользовательской функции [!INCLUDE[tsql](../../includes/tsql-md.md)] .

Вы используете пользовательскую функцию T-SQL _fnCalculateDistance_для вычисления расстояния по формуле гаверсинуса, а затем другую пользовательскую функцию T-SQL _fnEngineerFeatures_для создания таблицы, содержащей все характеристики.

### <a name="calculate-trip-distance-using-fncalculatedistance"></a>Вычисление расстояния поездок с помощью fnCalculateDistance

1.  Функция _fnCalculateDistance_ должна была быть загружена и зарегистрирована в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в рамках подготовки к работе с этим пошаговым руководством. Потратьте пару минут, чтобы ознакомиться с кодом.
  
    В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]последовательно разверните узлы **Программируемость**, **Функции** и **Скалярные функции**.
    Щелкните правой кнопкой мыши функцию _fnCalculateDistance_, а затем выберите команду **Изменить** , чтобы открыть скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в новом окне запроса.
  
    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function that calculates the direct distance between two geographical coordinates
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
**Примечания.**

- Функция является скалярной и возвращает одно значение предопределенного типа.
- Она принимает в качестве входных значений широту и долготу мест посадки и высадки. Формула гаверсинуса преобразует координаты в радианы и использует полученные значения для вычисления прямого расстояния в километрах между этими двумя местами.

Для добавления вычисленного значения в таблицу, которую можно использовать для обучения модели, применяется другая функция: _fnEngineerFeatures_.

### <a name="save-the-features-using-fnengineerfeatures"></a>Сохранение функций с помощью _fnEngineerFeatures_

1.  Изучите код пользовательской функции T-SQL _fnEngineerFeatures_, которая должна была быть создана для вас в рамках подготовки к работе с этим пошаговым руководством.
  
    Это табличная функция, которая принимает несколько столбцов в качестве входных значений и выводит таблицу с несколькими столбцами характеристик.  Назначение этой функции — создать набор характеристик, который будет использоваться при построении модели. Функция _fnEngineerFeatures_ вызывает ранее созданную функцию T-SQL _fnCalculateDistance_для получения прямого расстояния между местами посадки и высадки.
  
    ```sql
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
  
2. Чтобы убедиться в том, что эта функция работает, можно с ее помощью вычислить географическое расстояние поездок, для которых расстояние по счетчику было равно 0, но места посадки и высадки были разными.
  
    ```sql
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Как видите, расстояние по счетчику не всегда соответствует географическому расстоянию. Именно поэтому важно проектирование функций.

На следующем шаге вы узнаете, как использовать эти функции данных для создания и обучения модели машинного обучения с помощью Python.

## <a name="next-step"></a>Следующий шаг

[Обучение и сохранение модели Python с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Предыдущий шаг

[Просмотр и визуализация данных](sqldev-py3-explore-and-visualize-the-data.md)


