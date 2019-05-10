---
title: Учебник. Используйте редактор Transact-SQL для создания объектов базы данных
titleSuffix: Azure Data Studio
description: В этом учебнике показано ключевых функций в Azure Data Studio, которые упрощают работу с помощью T-SQL.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 3d227d308ba05a4c9336e2f5dcb728e85c18d7ed
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089704"
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Учебник. Используйте редактор Transact-SQL для создания объектов базы данных: [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Создание и выполнение запросов, хранимых процедур, сценарии и др. — основные задачи для специалистов по базам данных. В этом учебнике показано ключевых функций в редакторе T-SQL для создания объектов базы данных.

В этом руководстве вы узнаете, как использовать [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] для:
> [!div class="checklist"]
> * Поиск объектов базы данных
> * Изменение данных таблицы 
> * Использование фрагментов для быстрого написания T-SQL
> * Просмотр сведений о объекта базы данных с помощью *"Показать определение"* и *перейти к определению*


## <a name="prerequisites"></a>предварительные требования

В этом руководстве требуется SQL Server или базы данных SQL Azure *TutorialDB*. Чтобы создать *TutorialDB* базы данных, выполните одно из следующих кратких руководств:

- [Подключение и запрос SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключение и запрос базы данных SQL Azure с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Быстро найти объект базы данных и выполнять общие задачи

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] Предоставляет элемент поиска для быстрого поиска объектов базы данных. Список результатов предоставляет контекстное меню для распространенных задач, соответствующих выбранного объекта, такие как *изменение данных* для таблицы.

1. Откройте на боковой панели СЕРВЕРОВ (**Ctrl + G**), разверните **баз данных**и выберите **TutorialDB**. 

1. Откройте *панели мониторинга TutorialDB* щелкните правой кнопкой мыши **TutorialDB** и выбрав **управление** в контекстном меню:

   ![контекстное меню - Управление](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. На панели мониторинга, щелкните правой кнопкой мыши **dbo. Клиенты** (в мини-приложения поиска) и выберите **изменение данных**.
   
   > [!TIP]
   > Для баз данных с множеством объектов используйте мини-приложение поиска можно быстро найти таблицы, представления, и т.д., который вы ищете.

   ![Быстрый поиск мини-приложения](./media/tutorial-sql-editor/quick-search-widget.png)

1. Изменить **электронной почты** столбцов в первой строке, тип *orlando0@adventure-works.com*и нажмите клавишу **ввод** для сохранения изменений.

   ![Изменение данных](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Использование фрагментов кода T-SQL для создания хранимых процедур

[!INCLUDE[name-sos](../includes/name-sos-short.md)] предоставляет многие встроенные фрагменты кода T-SQL для быстрого создания инструкций.


1. Откройте новый редактор запросов, нажав клавишу **Ctrl + N**.

2. Тип **sql** в редакторе со стрелкой вниз до **sqlCreateStoredProcedure**и нажмите клавишу *вкладке* ключ (или *ввод*) для загрузки хранимых создания фрагмент кода для процедуры.

   ![список фрагментов](./media/tutorial-sql-editor/snippet-list.png)

3. Фрагмент кода хранимой процедуры создать имеет два поля для быстрого редактирования *StoredProcedureName* и *SchemaName*. Выберите *StoredProcedureName*, щелкните правой кнопкой мыши и выберите **всем вхождениям изменение**. Теперь введите *getCustomer* и все *StoredProcedureName* записей изменений для *getCustomer*.

   ![Фрагмент кода](./media/tutorial-sql-editor/snippet.png)

5. Замените все вхождения *SchemaName* для *dbo*. 
6. Параметры заполнителя и основной текст, который необходимо обновить, содержащийся во фрагменте. *EXECUTE* инструкция также содержит текст заполнителя, так как он не знает, какое количество параметров, процедура будет иметь. Для этого руководства об обновлении фрагмент кода таким образом он выглядит аналогично следующему коду:

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
    
5. Чтобы создать хранимую процедуру и присвойте ему тестового запуска, нажмите клавишу **F5**.

Теперь создается хранимая процедура и **РЕЗУЛЬТАТЫ** возвращенного клиента, отображаются в формате JSON. Чтобы просмотреть JSON отформатированы, щелкните возвращаемых записей. 


## <a name="use-peek-definition"></a>Используйте "Показать определение" 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] предоставляет возможность просматривать определение объектов, с помощью функции определения считывания. В этом разделе создается вторая хранимая процедура и использует "Показать определение" просмотреть столбцы в таблице, чтобы быстро создать текст хранимой процедуры.

1. Откройте новый редактор, нажав клавишу **Ctrl + N**. 

2. Тип *sql* в редакторе со стрелкой вниз до *sqlCreateStoredProcedure*и нажмите клавишу *вкладке* ключ (или *ввод*) для загрузки хранимых создания фрагмент кода для процедуры.
3. Введите в *setCustomer* для *StoredProcedureName* и *dbo* для *SchemaName*

3. Замените @param заполнители со следующим определением параметра:

   ```sql
   @json_val nvarchar(max)
   ```

4. Замените текст хранимой процедуры следующим кодом:
   ```sql
   INSERT INTO dbo.Customers
   ```

5. В *вставить* строки вы только что добавленную, щелкните правой кнопкой мыши **dbo. Клиенты** и выберите **"Показать определение"**.

   !["Показать определение"](./media/tutorial-sql-editor/peek-definition.png)

6. Определение таблицы появится, вы можете быстро просмотреть столбцы находятся в таблице. См. список столбцов, чтобы легко выполнить инструкции хранимой процедуры. Завершите создание инструкции INSERT, добавленную ранее для завершения тело хранимой процедуры и закрыть окне отображения определения:

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
7. Удалите (или закомментируйте) *EXECUTE* команды в нижней части запроса.
8. Весь оператор должен выглядеть аналогично следующему коду:

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

8. Чтобы создать *setCustomer* хранимой процедуры, нажмите клавишу **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Используйте сохранить результаты запроса как JSON для проверки этой setCustomer хранимой процедуры

*SetCustomer* хранимая процедура, созданная в предыдущем разделе требует JSON данные передавались в *@json_val* параметра. В этом разделе показано, как получить немного правильно сформированный JSON для передачи в параметр, чтобы вы могли тестировать хранимой процедуры.

1. В **СЕРВЕРЫ** боковой панели щелкните правой кнопкой мыши *dbo. Клиенты* таблицы и нажмите кнопку **ВЫДЕЛИТЬ 1000 ВЕРХНИХ строк**.

2. Выберите первую строку в представлении результатов, убедитесь, что выбран всю строку (номер 1 в крайнем левом столбце щелкните) и выберите **Сохранить как JSON**.  
3. Перейдите в расположение, помнят, чтобы можно было удалить файл более поздней версии (для настольных компьютеров в примере) и щелкните папку **Сохранить**. Открывает файл в формате JSON.

   ![сохранить в формате JSON.](./media/tutorial-sql-editor/save-as-json.png)

4. Выберите данные JSON в редакторе и скопируйте его.
5. Откройте новый редактор, нажав клавишу **Ctrl + N**.
6. Предыдущие шаги Показать, как можно легко получить правильно отформатированные данные, чтобы завершить вызов *setCustomer* процедуры. См. в следующем коде используется один и тот же формат JSON с новыми сведениями клиентов, чтобы мы могли тестировать *setCustomer* процедуры. Эта инструкция включает синтаксис для объявления параметра и запустить новый get и задания процедуры. Можно вставить скопированные данные из предыдущего раздела и изменить его, так что это так же, как приведенный ниже или просто вставьте следующую инструкцию в редакторе запросов.

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

7. Выполнение скрипта нажатием клавиши **F5**. Скрипт вставки данных нового клиента и возвращает сведения для нового клиента в формате JSON. Щелкните результат, чтобы открыть отформатированное представление.

   ![результат теста](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Следующие шаги
В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Объекты схемы для быстрого поиска
> * Изменение данных таблицы 
> * Написание скрипта T-SQL, с помощью фрагментов
> * Дополнительные сведения о объектов базы данных с помощью "Показать определение" и перейти к определению


Чтобы узнать, как включить **пять медленных запросов** мини-приложение, для работы с руководством далее:

> [!div class="nextstepaction"]
> [Включить анализ примера Медленные запросы мини-приложения](tutorial-qds-sql-server.md)
