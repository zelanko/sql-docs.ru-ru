---
title: "Учебник: Редактор SQL Studio операций (Предварительная версия) Transact-SQL для создания объектов базы данных | Документы Microsoft"
description: "Этот учебник демонстрирует основные возможности Studio операций SQL (Предварительная версия), которые упрощают использование T-SQL."
ms.custom: tools|sos
ms.date: 11/15/2017
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
ms.openlocfilehash: b2754a998963be5a25d00aa58dcb9b4105bb8f37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Учебник: Использование редактора Transact-SQL для создания объектов базы данных-[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Создание и выполнение запросов, хранимых процедур, сценарии, т. д. — основные задачи для специалистов по базам данных. Этот учебник демонстрирует ключевые функции в редакторе T-SQL для создания объектов базы данных.

В этом учебнике вы узнаете, как использовать [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] для:
> [!div class="checklist"]
> * Поиск объектов базы данных
> * Изменение данных таблицы 
> * Использование фрагментов для быстрого написания T-SQL
> * Просмотр сведений о объекта базы данных с помощью *Показать определение* и *перейти к определению*


## <a name="prerequisites"></a>предварительные требования

Упражнений этого учебника требуется SQL Server или база данных SQL Azure *TutorialDB*. Для создания *TutorialDB* базы данных, выполните одно из следующих краткие руководства:

- [Подключения и запроса с помощью SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключения и запроса с помощью базы данных SQL Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Быстро найти объект базы данных и выполнять общие задачи

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]Предоставляет элемент поиска для быстрого поиска объектов базы данных. Список результатов предоставляет контекстное меню для общих задач, которые важны для выбранного объекта, например *изменить данные* для таблицы.

1. Откройте на боковой панели СЕРВЕРОВ (**Ctrl + G**), разверните **баз данных**и выберите **TutorialDB**. 

1. Откройте *мониторинга TutorialDB* , выбрав **управление** в контекстном меню.

   ![контекстное меню: управление](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Найдите *клиентов* таблицу, введя *спользовать специальную* в мини-приложении поиска.
1. Щелкните правой кнопкой мыши **dbo. Клиенты** и выберите **изменения данных**.

   ![Быстрый поиск мини-приложения](./media/tutorial-sql-editor/quick-search-widget.png)

1. Изменить **электронной почты** столбцов в первой строке типа  *orlando0@adventure-works.com* и нажмите клавишу **ввод** для сохранения изменений.

   ![Изменение данных](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-a-stored-procedure"></a>Использование фрагментов кода T-SQL для создания хранимой процедуры

### <a name="use-snippets-in-includename-sos-shortincludesname-sos-shortmd"></a>Использование фрагментов в[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]

1. Откройте новый редактор запросов, нажав клавишу **Ctrl + N**.

2. Тип **sql** в редакторе со стрелкой вниз до **sqlCreateStoredProcedure**и нажмите клавишу *вкладке* ключ для загрузки нового фрагмента хранимой процедуры.

   ![список фрагментов](./media/tutorial-sql-editor/snippet-list.png)

3. Тип *getCustomer* и все *StoredProcedureName* записей изменений для *getCustomer*. 

   ![Фрагмент кода](./media/tutorial-sql-editor/snippet.png)

4. Замените rest хранимой процедуры T-SQL, ниже:

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
    SELECT  c.CustomerID, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerID = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Чтобы создать хранимую процедуру и присвойте ему тестового запуска, нажмите клавиши **F5**.

## <a name="use-peek-definition-and-go-to-definition"></a>Используйте быстрый просмотр определений и перейти к определению 

1. Откройте новый редактор, нажав клавиши **Ctrl + N**. 

2. Введите и выберите **sqlCreateStoredProcedure** в списке предложений фрагмент. Введите в **setCustomer** для **StoredProcedureName** и **dbo** для **SchemaName**

3. Замените @param строки со следующим определением параметра:

   ```sql
       @json_val nvarchar(max)
   ```

4. Замените текст хранимой процедуры следующим кодом:
   ```sql
   -- body of the stored procedure
   INSERT INTO dbo.Customers
   ```

5. Щелкните правой кнопкой мыши **dbo. Клиенты** и выберите **Показать определение**.

   ![Просмотр определения](./media/tutorial-sql-editor/peek-definition.png)

6. Для выполнения следующей инструкции insert используйте в определении таблицы.

   ```sql
   INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
   ```
7. Последняя инструкция должна быть:

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
       INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Чтобы выполнить скрипт, нажмите клавишу **F5**.

## <a name="use-save-query-results-as-json-to-test-our-stored-procedure"></a>Используйте сохранить результаты запроса как JSON для тестирования нашей хранимых процедур

1. **ВЫДЕЛИТЬ 1000 ВЕРХНИХ строк** из *dbo. Клиенты* таблицы.

2. Выберите первую строку в представление результатов и нажмите кнопку **сохранение JSON**.  
3. Нажмите кнопку **Сохранить**, и он открывает выделенную строку в формате JSON.

   ![сохранить в формате JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Выберите данные JSON и скопируйте его.

5. Открытие нового запроса для *TutorialDB* и выполнить следующий скрипт проверки использования данных JSON в качестве шаблона из предыдущего шага. Изменение значений для *CustomerID*, *имя*, *расположение*, и *электронной почты*.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerID": 5,
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


Чтобы узнать, как включить **пять самых медленных запросов** образец анализ, выполните следующее руководство:

> [!div class="nextstepaction"]
> [Включить мини-приложения образец анализ медленных запросов](tutorial-qds-sql-server.md)
