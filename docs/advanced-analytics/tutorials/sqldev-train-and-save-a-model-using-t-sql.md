---
title: Занятие 3. обучение и сохранение модели с помощью R и T-SQL
description: Учебник, демонстрирующий обучение, сериализацию и сохранение модели R с помощью SQL Server хранимых процедур и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f23f4c350855b71a3633587bb3c092988fe89fef
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715336"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Урок 3. Обучение и сохранение модели с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья является частью руководства для разработчиков SQL, посвященных использованию R в SQL Server.

На этом занятии вы узнаете, как обучить модель машинного обучения с помощью языка R. Вы обучите модель с помощью функций данных, созданных на предыдущем занятии, а затем сохраните обученную модель в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблице. В этом случае пакеты R уже установлены вместе с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], поэтому все может быть выполнено из SQL.

## <a name="create-the-stored-procedure"></a>Создание хранимой процедуры

При вызове R из T-SQL используется системная хранимая процедура [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Однако для процессов, которые повторяются часто, например для повторного обучения модели, проще инкапсулировать вызов sp_execute_exernal_script в другой хранимой процедуре.

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте новое окно **запроса** .

2. Выполните следующую инструкцию, чтобы создать хранимую процедуру **ркстраинлогитмодел**. Эта хранимая процедура определяет входные данные и использует **rxLogit** из RevoScaleR для создания модели логистической регрессии.

    ```sql
    CREATE PROCEDURE [dbo].[RxTrainLogitModel] (@trained_model varbinary(max) OUTPUT)
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
    
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model 
    trained_model <- as.raw(serialize(logitObj, NULL));
    ',
      @input_data_1 = @inquery,
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT; 
    END
    GO
    ```

    - Чтобы убедиться, что некоторые данные оставлены для тестирования модели, 70% данных выбираются случайным образом из таблицы данных такси в целях обучения.

    - Запрос SELECT использует пользовательскую скалярную функцию *fnCalculateDistance* для вычисления прямого расстояния между местами посадки и высадки. Результаты запроса хранятся в переменной ввода R по умолчанию, `InputDataset`.
  
    - Скрипт R вызывает функцию **rxLogit** , которая является одной из улучшенных функций R [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], включенных в, для создания модели логистической регрессии.
  
        Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик:  _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
  
    - Обученная модель, сохраненная в переменной `logitObj`R, сериализуется и возвращается в качестве выходного параметра.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Обучение и развертывание модели R с помощью хранимой процедуры

Поскольку хранимая процедура уже включает определение входных данных, не нужно указывать входной запрос.

1. Чтобы обучить и развернуть модель R, вызовите хранимую процедуру и вставьте ее в таблицу базы данных _nyc_taxi_models_, чтобы ее можно было использовать для будущих прогнозов:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Просмотрите [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] окно **сообщения** для сообщений, которые будут переданы в поток **stdout** для R, как это сообщение: 

    Сообщения STDOUT из внешнего скрипта: Считано строк: 1193025, всего обработано строк: 1193025, общее время фрагмента: 0,093 секунд "

    Можно также просмотреть сообщения, относящиеся к отдельной функции, `rxLogit`и отобразить переменные и тестовые метрики, созданные в ходе создания модели.

3.  После завершения выполнения инструкции откройте таблицу *nyc_taxi_models*. Обработка данных и подгонка модели может занять некоторое время.

    Видно, что была добавлена одна новая строка, которая содержит сериализованную модель в _модели_ столбца и имя модели **RxTrainLogit_model** в _имени_столбца.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

На следующем шаге будет использоваться обученная модель для создания прогнозов.

## <a name="next-lesson"></a>Следующее занятие

[Занятие 4. Прогнозирование возможных результатов с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 2. Создание функций данных с помощью функций R и T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

