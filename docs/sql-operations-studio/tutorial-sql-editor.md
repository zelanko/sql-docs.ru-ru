---
title: "Учебник: Редактор SQL Studio операций (Предварительная версия) Transact-SQL для создания объектов базы данных | Документы Microsoft"
description: "Этот учебник демонстрирует основные возможности Studio операций SQL (Предварительная версия), которые упрощают использование T-SQL."
ms.custom: tools|sos
ms.date: 03/13/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db9cc8185742980b649f9fcc11eced5687201464
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2018
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Учебник: Использование редактора Transact-SQL для создания объектов базы данных- [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Создание и выполнение запросов, хранимых процедур, сценарии, т. д. — основные задачи для специалистов по базам данных. Этот учебник демонстрирует ключевые функции в редакторе T-SQL для создания объектов базы данных.

В этом учебнике вы узнаете, как использовать [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] для:
> [!div class="checklist"]
> * Поиск объектов базы данных
> * Изменение данных таблицы 
> * Использование фрагментов для быстрого написания T-SQL
> * Просмотр сведений о объекта базы данных с помощью *Показать определение* и *перейти к определению*


## <a name="prerequisites"></a>предварительные требования

Упражнений этого учебника требуется SQL Server или база данных SQL Azure *TutorialDB*. Для создания *TutorialDB* базы данных, выполните одно из следующих краткие руководства:

- [Подключения и запроса с помощью SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключения и запроса с помощью базы данных SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Быстро найти объект базы данных и выполнять общие задачи

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] Предоставляет элемент поиска для быстрого поиска объектов базы данных. Список результатов предоставляет контекстное меню для общих задач, которые важны для выбранного объекта, например *изменить данные* для таблицы.

1. Откройте на боковой панели СЕРВЕРОВ (**Ctrl + G**), разверните **баз данных**и выберите **TutorialDB**. 

1. Откройте *мониторинга TutorialDB* щелкните правой кнопкой мыши **TutorialDB** и выбрав **управление** в контекстном меню:

   ![контекстное меню: управление](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. На панели мониторинга щелкните правой кнопкой мыши **dbo. Клиенты** (в мини-приложения поиска) и выберите **изменить данные**.
   
   > [!TIP]
   > Для баз данных с множеством объектов используйте мини-приложения поиска быстро найти таблицы, представления и т. д., который вы ищете.

   ![Быстрый поиск мини-приложения](./media/tutorial-sql-editor/quick-search-widget.png)

1. Изменить **электронной почты** столбцов в первой строке типа  *orlando0@adventure-works.com* и нажмите клавишу **ввод** для сохранения изменений.

   ![Изменение данных](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Использование фрагментов кода T-SQL для создания хранимых процедур

Операции SQL Studio предоставляет многие встроенные фрагменты кода T-SQL для быстрого создания инструкций.


1. Откройте новый редактор запросов, нажав клавишу **Ctrl + N**.

2. Тип **sql** в редакторе со стрелкой вниз до **sqlCreateStoredProcedure**и нажмите клавишу *вкладка* ключ (или *ввод*) для загрузки создания хранимых фрагмент кода для процедуры.

   ![список фрагментов](./media/tutorial-sql-editor/snippet-list.png)

3. Фрагмент кода хранимой процедуры создать имеет два поля для быстрого изменения *StoredProcedureName* и *SchemaName*. Выберите *StoredProcedureName*, щелкните правой кнопкой мыши и выберите **изменений всех вхождений**. Теперь введите *getCustomer* и все *StoredProcedureName* записей изменений для *getCustomer*.

   ![Фрагмент кода](./media/tutorial-sql-editor/snippet.png)

5. Замените все вхождения *SchemaName* для *dbo*. 
6. Во фрагменте заполнитель параметров и основной текст, который требуется обновить. *EXECUTE* инструкция содержит текст заполнителя, так как он не знает, какое количество параметров, процедура будет иметь. Для этого учебника обновите фрагмент так выглядит как следующий код:

    ```sql
    -- Create a new stored procedure called 'getCustomer' in schema 'dbo'
    -- Drop the stored procedure if it already exists
    IF EXISTS (
    SELECT *
    FROM INFORMATION_SCHEMA.ROUTINES
    WHERE SPECIFIC_SCHEMA = N'dbo'
    AND SPECIFIC_NAME = N'getCustomer'
    )
    DROP PROCEDURE dbo.getCustomer
    GO
    -- Create the stored procedure in the specified schema
    CREATE PROCEDURE dbo.getCustomer
    @ID int
    -- add more stored procedure parameters here
    AS
    -- body of the stored procedure
    SELECT  c.CustomerId, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerId = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Чтобы создать хранимую процедуру и присвойте ему тестового запуска, нажмите клавиши **F5**.

Теперь создается хранимая процедура и **РЕЗУЛЬТАТОВ** отображаются возвращаемый клиенту в формате JSON. Чтобы увидеть отформатированную JSON, щелкните возвращенной записи. 


## <a name="use-peek-definition"></a>Использование определения показа 

Операции SQL Studio предоставляет возможность просмотреть определение объектов с помощью функции определения считывания. В этом разделе создает вторую хранимую процедуру и использует определения считывания для Узнайте, какие столбцы в таблице, чтобы быстро создать тело хранимой процедуры.

1. Откройте новый редактор, нажав клавиши **Ctrl + N**. 

2. Тип *sql* в редакторе со стрелкой вниз до *sqlCreateStoredProcedure*и нажмите клавишу *вкладка* ключ (или *ввод*) для загрузки создания хранимых фрагмент кода для процедуры.
3. Введите в *setCustomer* для *StoredProcedureName* и *dbo* для *SchemaName*

3. Замените @param местозаполнителей следующее определение параметра:

   ```sql
   @json_val nvarchar(max)
   ```

4. Замените текст хранимой процедуры с помощью следующего кода:
   ```sql
   INSERT INTO dbo.Customers
   ```

5. В *вставить* строки, то щелкните правой кнопкой мыши только что добавленную **dbo. Клиенты** и выберите **Показать определение**.

   ![Просмотр определения](./media/tutorial-sql-editor/peek-definition.png)

6. Определение таблицы появится, можно быстро понять, какие столбцы расположены в таблице. См. список столбцов, чтобы легко выполнить инструкции для хранимой процедуры. Завершите создание ранее добавлены для завершения тело хранимой процедуры и закройте окно просмотра определения инструкции INSERT:

   ```sql
   INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
    )
   ```
7. Удалите (или закомментируйте) *EXECUTE* команд в нижней части запроса.
8. Выполнение всей инструкции выглядит как следующий код:

   ```sql
   -- Create a new stored procedure called 'setCustomer' in schema 'dbo'
   -- Drop the stored procedure if it already exists
   IF EXISTS (
   SELECT *
       FROM INFORMATION_SCHEMA.ROUTINES
       WHERE SPECIFIC_SCHEMA = N'dbo'
       AND SPECIFIC_NAME = N'setCustomer'
   )
   DROP PROCEDURE dbo.setCustomer
   GO
   -- Create the stored procedure in the specified schema
   CREATE PROCEDURE dbo.setCustomer
       @json_val nvarchar(max) 
   AS
       -- body of the stored procedure
       INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Для создания *setCustomer* хранимой процедуры, нажмите клавишу **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Используйте сохранить результаты запроса как JSON для проверки setCustomer хранимой процедуры

*SetCustomer* хранимая процедура, созданная в предыдущем разделе требует JSON данные передавались в  *@json_val*  параметра. В этом разделе показано, как получить немного правильно отформатированную JSON для передачи в параметр, можно выполнить хранимую процедуру.

1. В **СЕРВЕРЫ** боковой панели щелкните правой кнопкой мыши *dbo. Клиенты* и нажмите кнопку **ВЫДЕЛИТЬ 1000 ВЕРХНИХ строк**.

2. Выберите первую строку в представлении результатов, убедитесь, что выбран вся строка (значение 1 в столбце слева щелкните) и выберите **сохранение JSON**.  
3. Изменить папку в расположении, вы будете помните, чтобы можно было удалить файл более поздней версии (для настольных компьютеров примере) и нажмите кнопку **Сохранить**. Открывает файл в формате JSON.

   ![сохранить в формате JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Выберите данные JSON в редакторе и скопируйте его.
5. Откройте новый редактор, нажав клавиши **Ctrl + N**.
6. Предыдущие шаги Показать, как можно легко получить правильно отформатированные данные, чтобы завершить вызов *setCustomer* процедуры. Вы увидите следующий код использует тот же формат JSON с новые сведения о клиенте, чтобы мы смогли проверить *setCustomer* процедуры. Эта инструкция включает синтаксис для объявления параметра и запустить новый get и задания процедуры. Можно вставить скопированные данные из предыдущего раздела и изменить его так же, как приведенный ниже пример или просто вставьте следующую инструкцию в редакторе запросов.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerId": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. Выполнить скрипт, нажав клавишу **F5**. Скрипт вставляет новый клиент и возвращает информацию нового клиента в формате JSON. Щелкните результат, чтобы открыть форматированного представления.

   ![Результат тестирования](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Следующие шаги
В этом учебнике вы узнали, как:
> [!div class="checklist"]
> * Объекты схемы быстрого поиска
> * Изменение данных таблицы 
> * Написание скрипта T-SQL, с помощью фрагментов кода
> * Дополнительные сведения о объектов базы данных с помощью Показать определение и перейти к определению


Чтобы узнать, как включить **пять самых медленных запросов** мини-приложение, выполните следующее руководство:

> [!div class="nextstepaction"]
> [Включить мини-приложения образец анализ медленных запросов](tutorial-qds-sql-server.md)
