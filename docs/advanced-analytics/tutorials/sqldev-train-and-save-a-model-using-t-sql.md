---
title: 'Занятие 3 обучение и сохранение модели с помощью R и T-SQL: машинного обучения SQL Server'
description: Учебник, демонстрирующий обучения, сериализации и сохранения модели R с помощью SQL Server хранимых процедур и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a76a3a77f3c258372e6ff3a7e472b472fcc2f073
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510011"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Урок 3. Обучение и сохранение модели с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит руководства для разработчиков SQL по использованию R в SQL Server.

На этом занятии вы узнаете, как обучить модель машинного обучения с помощью языка R. Вы будете обучить модель, используя функции данных, созданный на предыдущем занятии, а затем сохраните обученную модель в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. В этом случае пакеты R уже установлены с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], поэтому все, что можно сделать с SQL.

## <a name="create-the-stored-procedure"></a>Создайте хранимую процедуру

При вызове R из T-SQL, можно использовать системную хранимую процедуру, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Тем не менее для процессов, которые часто повторяются например повторное Обучение модели, проще инкапсулировать вызов процедуры sp_execute_exernal_script в другой хранимой процедуры.

1. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новую **запроса** окна.

2. Выполните следующую инструкцию, чтобы создать хранимую процедуру **RxTrainLogitModel**. Эта хранимая процедура определяет входные данные и использует **rxLogit** из RevoScaleR для создания модели логистической регрессии.

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

    - Чтобы убедиться, что некоторые данные, оставшиеся для проверки модели, 70% данных выбираются в случайном порядке из таблицы данных о поездках в такси в учебных целях.

    - Запрос SELECT использует пользовательскую скалярную функцию *fnCalculateDistance* для вычисления прямого расстояния между местами посадки и высадки. результаты запроса сохраняются в входной переменной R по умолчанию, `InputDataset`.
  
    - Скрипт R вызывает **rxLogit** функцию, которая является одним из расширенных функций R в состав [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], чтобы создать модель логистической регрессии.
  
        Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик:  _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
  
    - Обученной модели, сохраненные в переменной R `logitObj`, сериализуется и возвращается как выходной параметр.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Обучать и развертывать модели R, с помощью хранимой процедуры

Так как хранимая процедура уже включает в себя определение входных данных, входной запрос указывать не нужно.

1. Обучать и развертывать модели R, вызовите хранимую процедуру и вставить их в таблицу базы данных _nyc_taxi_models_, таким образом, чтобы его можно использовать для будущих прогнозов:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Контрольные значения **сообщений** окно [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для сообщений, которые должны передаваться в R **stdout** потока, как это сообщение: 

    «Сообщения STDOUT из внешнего скрипта: Строк считано: 1193025, всего строк обработано: Время 1193025, всего блока: 0,093 сек»

    Может также появиться сообщения, относящиеся к отдельной функции `rxLogit`, отображение переменных и проверить метрики, созданные в процессе создания модели.

3.  При завершении выполнения инструкции, откройте таблицу *nyc_taxi_models*. Обработка данных и компоновка модели может занять некоторое время.

    Можно увидеть, был добавлен, одну новую строку, которая содержит сериализованную модель в столбце _модели_ и имя модели **RxTrainLogit_model** в столбце _имя_.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

На следующем шаге вы используете обученную модель для создания прогнозов.

## <a name="next-lesson"></a>Следующее занятие

[Занятие 4. Предсказания возможных результатов, с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 2. Создание функций данных с помощью функции R и T-SQL](..//tutorials/sqldev-create-data-features-using-t-sql.md)

