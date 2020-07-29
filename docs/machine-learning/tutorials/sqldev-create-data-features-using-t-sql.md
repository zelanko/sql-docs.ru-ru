---
title: Учебник по R и T-SQL. Характеристики данных
description: Учебник по добавлению вычислений в хранимые процедуры для использования в моделях машинного обучения R.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c5b588f9cb94d39753040e3251d9a4b2e1f12d49
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85670953"
---
# <a name="lesson-2-create-data-features-using-r-and-t-sql"></a>Урок 2. Создание признаков данных с помощью R и T-SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта статья является частью учебника для разработчиков SQL с инструкциями по использованию R в SQL Server.

На этом этапе вы научитесь создавать характеристики на основе необработанных данных с помощью функции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

## <a name="about-feature-engineering"></a>Сведения о формировании признаков

После нескольких циклов исследования данных вы собрали определенной объем аналитической информации и готовы переходить к *формированию характеристик*. Процесс создания значимых признаков на основе необработанных данных — важнейший этап при создании аналитических моделей.

В этом наборе данных значения расстояний основаны на показаниях счетчиков и необязательно отражают расстояние по карте или фактическое расстояние поездки. Поэтому необходимо вычислить прямое расстояние между местами посадки и высадки с помощью координат, доступных в исходном наборе данных по работе такси в Нью-Йорке. Это можно сделать с помощью [формулы гаверсинуса](https://en.wikipedia.org/wiki/Haversine_formula) в пользовательской функции [!INCLUDE[tsql](../../includes/tsql-md.md)] .

Вы используете пользовательскую функцию T-SQL _fnCalculateDistance_для вычисления расстояния по формуле гаверсинуса, а затем другую пользовательскую функцию T-SQL _fnEngineerFeatures_для создания таблицы, содержащей все характеристики.

В общем виде процесс выглядит так:

- создание функции T-SQL, выполняющей вычисления;

- вызов функции для создания данных признаков;

- сохранение данных признаков в таблице.

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Вычисление расстояния поездки с помощью функции fnCalculateDistance

Функция _fnCalculateDistance_ должна была быть скачана и зарегистрирована в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в рамках подготовки к работе с этим учебником. Вкратце изучите код.
  
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

## <a name="generate-the-features-using-_fnengineerfeatures_"></a>Формирование признаков с помощью функции _fnEngineerFeatures_

Для добавления вычисленных значений в таблицу, которую можно использовать для обучения модели, применяется другая функция: _fnEngineerFeatures_. Эта новая функция вызывает ранее созданную функцию T-SQL _fnCalculateDistance_ для получения прямого расстояния между местами посадки и высадки. 

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

    + Эта функция с табличным значением принимает несколько столбцов в качестве входных данных и выводит таблицу с несколькими столбцами признаков.

    + Назначение этой функции — создать признаки, которые будут использоваться при построении модели.

2.  Чтобы убедиться в том, что эта функция работает, вычислите с ее помощью географическое расстояние поездок, для которых расстояние по счетчику было равно 0, но места посадки и высадки были разными.
  
    ```sql
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Как видите, расстояние по счетчику не всегда соответствует географическому расстоянию. Вот почему формирование характеристик имеет такое важное значение. Эти улучшенные признаки можно использовать для обучения модели машинного обучения с помощью языка R.

## <a name="next-lesson"></a>Следующее занятие

[Урок 3. Обучение и сохранение модели с помощью T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 1. Изучение и визуализация данных с помощью языка R и хранимых процедур](sqldev-explore-and-visualize-the-data.md)
