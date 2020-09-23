---
title: Учебник по R. Обучение и сохранение модели
titleSuffix: SQL machine learning
description: В четвертой части этого цикла учебников вы обучите и сохраните модель, используя R и Transact-SQL на SQL Server с помощью машинного обучения SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||>=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 242835f4ae65fa0f2ada862e225df47e35f8ec82
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88178441"
---
# <a name="r-tutorial-train-and-save-model"></a>Учебник по R. Обучение и сохранение модели
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

В четвертой части серии руководств вы узнаете, как обучить модель машинного обучения с использованием языка R. Модель будет обучена с помощью функций обработки данных, созданных в предыдущей части, а затем сохранена в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом случае пакеты R уже установлены в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], поэтому все действия можно выполнить с помощью SQL.

Работая с этой статьей, вы узнаете о следующем.

> [!div class="checklist"]
> + Создание и обучение модели с помощью хранимой процедуры SQL
> + Сохранение обученной модели в таблице SQL

В [первой части](r-taxi-classification-introduction.md) были установлены необходимые компоненты и восстановлена демонстрационная база данных.

Во [второй части](r-taxi-classification-explore-data.md) вы узнали, как проверить пример данных и создать несколько графиков.

В [третьей части](r-taxi-classification-create-features.md) вы узнали, как создавать функции из необработанных данных с помощью функции Transact-SQL. Затем вы вызвали эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

Из [пятой части](r-taxi-classification-deploy-model.md) вы узнаете, как ввести в эксплуатацию модели, которые были обучены и сохранены в соответствии с инструкциями в четвертой части.

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

   + Чтобы оставить часть данных для тестирования модели, из таблицы данных по работе такси случайным образом выбирается 70 % данных, которые будут использованы для обучения.

   + Запрос SELECT использует пользовательскую скалярную функцию *fnCalculateDistance* для вычисления прямого расстояния между местами посадки и высадки. Результаты выполнения запроса сохраняются во входной переменной R по умолчанию `InputDataset`.
  
   + Сценарий R вызывает функцию **rxLogit** (одну из расширенных функций R, входящих в состав служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]) для создания модели логистической регрессии.
  
     Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик:  _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
  
   + Модель обучения, сохраненная в переменной R `logitObj`, сериализуется и возвращается в качестве выходного параметра.

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

3. После выполнения инструкции откройте таблицу *nyc_taxi_models*. Обработка данных и компоновка модели может занять некоторое время.

   Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_ и имя модели **RxTrainLogit_model** в столбце _name_.

   ```text
   model                        name
   ---------------------------- ------------------
   0x580A00000002000302020....  RxTrainLogit_model
   ```

В следующей части этого учебника обученная модель будет использоваться для создания прогнозов.

## <a name="next-steps"></a>Дальнейшие шаги

Работая с этой статьей, вы выполните следующие задачи:

> [!div class="checklist"]
> + Создание и обучение модели с помощью хранимой процедуры SQL
> + Обученная модель сохранена в таблице SQL

> [!div class="nextstepaction"]
> [Учебник по R. Запуск прогнозов в хранимых процедурах SQL](r-taxi-classification-deploy-model.md)
