---
title: "Шаг&#160;5. Обучение и сохранение модели с помощью T-SQL (учебник по дополнительным аналитическим функциям в базе данных) | Microsoft Docs"
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
ms.assetid: 3282e8ed-b515-4ed5-8543-fcef68629a92
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Шаг&#160;5. Обучение и сохранение модели с помощью T-SQL (учебник по дополнительным аналитическим функциям в базе данных)
В этом шаге вы узнаете, как обучить модель машинного обучения с помощью языка R. Пакеты R уже установлены вместе со службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], что позволяет вызывать алгоритм из хранимой процедуры. Вы обучите модель с помощью только что созданных характеристик данных, а затем сохраните обученную модель в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Создание модели R с помощью хранимых процедур  
Все вызовы среды выполнения R, которая устанавливается со службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], выполняются с помощью системной хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Однако если нужно переобучить модель, возможно, будет проще инкапсулировать вызов процедуры sp_execute_exernal_script в другой хранимой процедуре.  
  
В этом разделе вы создадите хранимую процедуру, которую можно использовать для построения модели с помощью данных, которые вы уже подготовили. Эта хранимая процедура определяет входные данные и использует пакет R для создания модели логистической регрессии.  
  
#### Создание хранимой процедуры  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] откройте новое окно запроса и выполните приведенную ниже инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModel_.  
  
    Обратите внимание на то, что, поскольку хранимая процедура уже включает в себя определение входных данных, входной запрос указывать не требуется.  
  
    ```  
    CREATE PROCEDURE [dbo].[TrainTipPredictionModel]  
  
    AS  
    BEGIN  
      DECLARE @inquery nvarchar(max) = N'  
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,   
        pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance  
        from nyctaxi_sample  
        tablesample (70 percent) repeatable (98052)  
    '  
      -- Insert the trained model into a database table  
      INSERT INTO nyc_taxi_models  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
  
    ## Create model  
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)  
    summary(logitObj)  
  
    ## Serialize model and put it in data frame  
    trained_model <- data.frame(model=as.raw(serialize(logitObj, NULL)));  
    ',  
                                      @input_data_1 = @inquery,  
                                      @output_data_1_name = N'trained_model'  
      ;  
  
    END  
    GO  
  
    ```  
  
    В рамках обучения модели эта хранимая процедура выполняет указанные ниже действия.  
  
    -   Чтобы часть данных осталась для тестирования модели, из таблицы данных по работе такси случайным образом выбирается 70 % данных.  
  
    -   Запрос SELECT использует пользовательскую скалярную функцию _fnCalculateDistance_ для вычисления прямого расстояния между местами посадки и высадки.  Результаты выполнения запроса сохраняются во входной переменной R по умолчанию `InputDataset`.  
  
    -   Скрипт R вызывает функцию `rxLogit` (одну из расширенных функций R, входящих в состав служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]) для создания модели логистической регрессии.  
  
        Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик: _passenger_count_, _trip_distance_, _trip_time_in_secs_ и _direct_distance_.  
  
    -   Модель обучения, сохраненная в переменной R `logitObj`, сериализуется и помещается в кадр данных для вывода в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выходные данные вставляются в таблицу _nyc_taxi_models_ базы данных, чтобы их можно было использовать для составления прогнозов в будущем.  
  
2.  Выполните инструкцию, чтобы создать хранимую процедуру.  
  
#### Создание модели R с помощью хранимой процедуры  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните приведенную ниже инструкцию.  
  
    ```  
    EXEC TrainTipPredictionModel  
    ```  
  
    Обработка данных и компоновка модели может занять некоторое время. Сообщения, которые должны передаваться в поток R **stdout**, отображаются в окне **Сообщения** среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Например:  
  
  
*Сообщения STDOUT из внешнего скрипта: Считано строк: 1193025, Всего обработано строк: 1193025, Всего времени на блок: 0,093 сек*       
  
Допустимые блоки данных считываются и обрабатываются. Также можно увидеть сообщения, относящиеся к отдельной функции `rxLogit`, в которых указывается переменная и показатели теста.  
  
2.  Откройте таблицу *nyc_taxi_models*. Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.  
  
  
  
*модель*  
*0x580A00000002000302020....*  
  
В следующем шаге вы используете обученную модель для создания прогнозов.  
  
## Следующий шаг  
[Шаг 6. Ввод модели в эксплуатацию](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md)  
  
## Предыдущий шаг  
[Шаг 4. Создание характеристик данных с помощью T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## См. также:  
[Дополнительные аналитические функции в базе данных для разработчиков SQL (учебник)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Учебники по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
