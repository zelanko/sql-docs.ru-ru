---
title: Урок 2 функций создания данных, с помощью функции R и T-SQL - машинного обучения SQL Server
description: Учебник, в котором показано, как добавить вычисления для хранимых процедур для использования в моделях R машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5d304bdf03eaea53ede0cf4b2f8d82f64c3d1021
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961924"
---
# <a name="lesson-2-create-data-features-using-r-and-t-sql"></a>Урок 2. Создание функций данных с помощью R и T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит руководства для разработчиков SQL по использованию R в SQL Server.

На этом этапе вы научитесь создавать характеристики на основе необработанных данных с помощью функции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

## <a name="about-feature-engineering"></a>О признаков

После нескольких циклов исследования данных вы собрали определенной объем аналитической информации и готовы переходить к *формированию характеристик*. Этот процесс создания характеристик из необработанных данных является важным шагом в создании аналитических моделей.

В этом наборе данных значения расстояний основаны на показаниях счетчиков и необязательно отражают расстояние по карте или фактическое расстояние поездки. Поэтому необходимо вычислить прямое расстояние между местами посадки и высадки с помощью координат, доступных в исходном наборе данных по работе такси в Нью-Йорке. Это можно сделать с помощью [формулы гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula) в пользовательской функции [!INCLUDE[tsql](../../includes/tsql-md.md)] .

Вы используете пользовательскую функцию T-SQL _fnCalculateDistance_для вычисления расстояния по формуле гаверсинуса, а затем другую пользовательскую функцию T-SQL _fnEngineerFeatures_для создания таблицы, содержащей все характеристики.

Общий процесс выглядит следующим образом:

- Создайте функцию T-SQL, которая выполняет вычисления

- Вызовите функцию для создания компонентов данных

- Сохранять данные в таблицу

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Вычисление расстояния поездки с помощью функции fnCalculateDistance

Функция _fnCalculateDistance_ должны были загружены и зарегистрированы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в процессе подготовки к работе с учебником. Внимательно изучите код.
  
1. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]последовательно разверните узлы **Программируемость**, **Функции** и **Скалярные функции**.   

2. Щелкните правой кнопкой мыши функцию _fnCalculateDistance_, а затем выберите команду **Изменить** , чтобы открыть скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в новом окне запроса.
  
    ```sql
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
  
    - Функция является скалярной и возвращает одно значение предопределенного типа.
  
    - Она принимает в качестве входных значений широту и долготу мест посадки и высадки. Формула гаверсинуса преобразует координаты в радианы и использует полученные значения для вычисления прямого расстояния в километрах между этими двумя местами.

## <a name="generate-the-features-using-fnengineerfeatures"></a>Создавать функции, с помощью _fnEngineerFeatures_

Чтобы добавить вычисляемые значения в таблицу, который может использоваться для обучения модели, вы используете другую функцию _fnEngineerFeatures_. Новая функция вызывает ранее созданную функцию T-SQL, _fnCalculateDistance_, для получения прямого расстояния между местами посадки и высадки. 

1. Изучите код пользовательской функции T-SQL _fnEngineerFeatures_, которая должна была быть создана для вас в рамках подготовки к работе с этим пошаговым руководством.
  
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

    + Возвращающие табличные значения функции, принимает несколько столбцов в качестве входных данных и выводит таблицу с несколькими столбцами характеристик.

    + Эта функция предназначена для создания новых функций для использования при построении модели.

2.  Чтобы убедиться, что эта функция работает, используйте его для вычисления географическое Расстояние поездок где расстояние по счетчику было равно 0, но места посадки и высадки были разными, для.
  
    ```sql
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Как видите, расстояние по счетчику не всегда соответствует географическому расстоянию. Вот почему формирование характеристик имеет такое важное значение. Эти функции улучшенные данных можно использовать для обучения модели машинного обучения с помощью языка R.

## <a name="next-lesson"></a>Следующее занятие

[Занятие 3. Обучение и сохранение модели с помощью T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 1. Анализ и визуализация данных с помощью R и хранимых процедур](sqldev-explore-and-visualize-the-data.md)
