---
title: Учебник по R и T-SQL. Обучение модели
description: Учебник, демонстрирующий обучение, сериализацию и сохранение модели R с помощью хранимых процедур SQL Server и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 406f8e1c60c5820f9edaaf7760b7aeed321d2611
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81115787"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Урок 3. Обучение и сохранение модели с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья является частью учебника для разработчиков SQL с инструкциями по использованию R в SQL Server.

На этом занятии вы узнаете, как обучить модель машинного обучения с использованием языка R. Модель будет обучена с помощью функций обработки данных, созданных на предыдущем занятии, а затем сохранена в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом случае пакеты R уже установлены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], поэтому все действия можно выполнить с помощью SQL.

## <a name="create-the-stored-procedure"></a>Создание хранимой процедуры

При вызове R из T-SQL используется системная хранимая процедура [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Однако для часто повторяемых процессов (например, повторное обучение модели) проще инкапсулировать вызов процедуры sp_execute_exernal_script в другую хранимую процедуру.

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] откройте новое окно **Запрос**.

2. Выполните следующую инструкцию, чтобы создать хранимую процедуру **RxTrainLogitModel**. Эта хранимая процедура определяет входные данные и использует функцию **rxLogit** из RevoScaleR для создания модели логистической регрессии.

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

    - Чтобы оставить часть данных для тестирования модели, из таблицы данных по работе такси случайным образом выбирается 70 % данных, которые будут использованы для обучения.

    - Запрос SELECT использует пользовательскую скалярную функцию *fnCalculateDistance* для вычисления прямого расстояния между местами посадки и высадки. Результаты выполнения запроса сохраняются во входной переменной R по умолчанию `InputDataset`.
  
    - Сценарий R вызывает функцию **rxLogit** (одну из расширенных функций R, входящих в состав служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]) для создания модели логистической регрессии.
  
        Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик:  _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
  
    - Модель обучения, сохраненная в переменной R `logitObj`, сериализуется и возвращается в качестве выходного параметра.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Обучение и развертывание модели R с помощью хранимой процедуры

Поскольку хранимая процедура уже включает в себя определение входных данных, указывать входной запрос не требуется.

1. Для обучения и развертывания модели R вызовите хранимую процедуру и вставьте ее в таблицу базы данных _nyc_taxi_models_, чтобы ее можно было использовать для будущих прогнозов:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Следите за сообщениями, которые должны передаваться в поток R **stdout**, в окне **Сообщения** среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]: 

    "Сообщения STDOUT из внешнего сценария: Прочитано строк: 1193025, всего обработано строк: 1193025, общее время обработки блока: 0,093 с"

    Также можно увидеть сообщения, относящиеся к отдельной функции `rxLogit`. В этих сообщениях указываются переменные и тестовые метрики, сформированные в ходе создания модели.

3.  После выполнения инструкции откройте таблицу *nyc_taxi_models*. Обработка данных и компоновка модели может занять некоторое время.

    Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_ и имя модели **RxTrainLogit_model** в столбце _name_.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

В следующем шаге вы используете обученную модель для создания прогнозов.

## <a name="next-lesson"></a>Следующее занятие

[Занятие 4. Прогнозирование возможных результатов с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 2. Формирование характеристик данных с помощью сценария R и функций T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

