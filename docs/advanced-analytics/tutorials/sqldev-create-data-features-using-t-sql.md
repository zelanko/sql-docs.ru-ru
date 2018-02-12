---
title: "Занятие 4: Создание компонентов данных, с помощью T-SQL | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 5b2f4c44-6192-40df-abf1-fc983844f1d0
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5802fe172f8476d11a776b15fd2038ebc6917eaf
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="lesson-4-create-data-features-using-t-sql"></a>Занятие 4: Создание компонентов данных, с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом этапе вы научитесь создавать характеристики на основе необработанных данных с помощью функции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

## <a name="about-feature-engineering"></a>О конструируются

После нескольких циклов исследования данных вы собрали определенной объем аналитической информации и готовы переходить к *формированию характеристик*. Этот процесс создания значимых признаков на основе необработанных данных является важным этапом в создании аналитических моделей.

В этом наборе данных значения расстояние основаны на обнаруженную индикатор расстояние и не обязательно представляет географические расстояния или фактическое расстояние. Поэтому необходимо вычислить прямое расстояние между местами посадки и высадки с помощью координат, доступных в исходном наборе данных по работе такси в Нью-Йорке. Это можно сделать с помощью [формулы гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula) в пользовательской функции [!INCLUDE[tsql](../../includes/tsql-md.md)] .

Вы используете пользовательскую функцию T-SQL _fnCalculateDistance_для вычисления расстояния по формуле гаверсинуса, а затем другую пользовательскую функцию T-SQL _fnEngineerFeatures_для создания таблицы, содержащей все характеристики.

Общий процесс выглядит следующим образом:

- Создайте функцию T-SQL, которая выполняет вычисления

- Вызов функции для создания данных, функция

- Сохранить данные в таблицу

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Вычисление расстояния маршрута с помощью fnCalculateDistance

Функция _fnCalculateDistance_ должны были загружены и зарегистрированы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в ходе подготовки для этого учебника. Внимательно просмотрите код.
  
1. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]последовательно разверните узлы **Программируемость**, **Функции** и **Скалярные функции**.   

2. Щелкните правой кнопкой мыши функцию _fnCalculateDistance_, а затем выберите команду **Изменить** , чтобы открыть скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] в новом окне запроса.
  
    ```SQL
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

## <a name="generate-the-features-using-fnengineerfeatures"></a>Создание функции с помощью _fnEngineerFeatures_

Чтобы добавить вычисляемые значения в таблицу, которая может использоваться для обучения модели, будет использоваться другой функции _fnEngineerFeatures_. Новая функция вызывает функцию ранее созданный T-SQL, _fnCalculateDistance_, чтобы получить прямой расстояние между приняли и истощение расположений. 

1. Изучите код пользовательской функции T-SQL _fnEngineerFeatures_, которая должна была быть создана для вас в рамках подготовки к работе с этим пошаговым руководством.
  
    ```SQL
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

    + Возвращающие табличные значения функции, принимает несколько столбцов в качестве входных данных и возвращает таблицу с несколькими столбцами компонентов.

    + Эта функция предназначена для создания новых функций для использования при построении модели.

2.  Чтобы убедиться, что эта функция работает, используйте его для вычисления географических расстояния для этих поездок, где расстояние отслеживаемой было равно 0, но расположения отправки и истощение указаны разные.
  
    ```SQL
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Как видите, расстояние по счетчику не всегда соответствует географическому расстоянию. Вот почему формирование характеристик имеет такое важное значение. Можно использовать эти функции повышения данных для обучения модели машинного обучения с помощью языка R.

## <a name="next-lesson"></a>Следующее занятие

[Занятие 5: Обучения и сохранить модель с помощью T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 3: Анализ и визуализация данных](../tutorials/sqldev-explore-and-visualize-the-data.md)
