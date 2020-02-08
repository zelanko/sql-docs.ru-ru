---
title: Создание объектов базы данных с помощью редактора Transact-SQL
titleSuffix: Azure Data Studio
description: В этом руководстве демонстрируются основные функции Azure Data Studio, упрощающие работу с T-SQL.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: 65f078c16080f9ae54563acb5bd21c50d2036057
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957038"
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Руководство. Создание объектов базы данных с помощью редактора Transact-SQL — [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Создание и выполнение запросов, хранимых процедур, скриптов и т. д. — основные задачи специалистов по базам данных. В этом руководстве демонстрируются основные функции редактора T-SQL для создания объектов базы данных.

В этом руководстве вы узнаете, как с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] выполнять следующие задачи:
> [!div class="checklist"]
> * поиск объектов базы данных;
> * изменение данных таблицы; 
> * использование фрагментов кода для быстрого написания инструкций T-SQL;
> * просмотр сведений об объектах базы данных с помощью функций *Показать определение* и *Перейти к определению*.


## <a name="prerequisites"></a>Предварительные требования

Для работы с этим руководством требуется SQL Server или база данных SQL Azure *TutorialDB*. Чтобы создать базу данных *TutorialDB*, выполните инструкции, приведенные в одном из следующих кратких руководств:

- [Подключение и отправка запроса к SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключение и отправка запроса к базе данных SQL Azure с помощью[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Быстрое нахождение объекта базы данных и выполнение стандартной задачи

В [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] имеется мини-приложение поиска, позволяющее быстро находить объекты базы данных. Контекстное меню в списке результатов содержит стандартные задачи, относящиеся к выбранному объекту, например *Изменить данные* для таблицы.

1. Откройте боковую панель "Серверы" (**CTRL+G**), разверните узел **Базы данных** и выберите базу данных **TutorialDB**. 

1. Откройте *панель мониторинга базы данных TutorialDB*, щелкнув базу данных **TutorialDB** правой кнопкой мыши и выбрав в контекстном меню пункт **Управление**.

   ![контекстное меню — пункт "Управление"](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. На панели мониторинга щелкните правой кнопкой мыши таблицу **dbo.Customers** (в мини-приложении поиска) и выберите пункт **Изменить данные**.
   
   > [!TIP]
   > Если база данных содержит множество объектов, мини-приложение поиска позволяет быстро находить искомые таблицы, представления и т. д.

   ![мини-приложение быстрого поиска](./media/tutorial-sql-editor/quick-search-widget.png)

1. Измените значение в первой строке столбца **Email** (Адрес электронной почты), введите *orlando0\@adventure-works.com* и нажмите клавишу **ВВОД**, чтобы сохранить изменение.

   ![изменение данных](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Создание хранимых процедур с помощью фрагментов кода T-SQL

В [!INCLUDE[name-sos](../includes/name-sos-short.md)] есть множество встроенных фрагментов кода T-SQL для быстрого создания инструкций.


1. Откройте новое окно редактора запросов, нажав клавиши **CTRL+N**.

2. Введите в редакторе строку **sql**, с помощью клавиши со стрелкой вниз перейдите к пункту **sqlCreateStoredProcedure** и нажмите клавишу *TAB* (или *ВВОД*), чтобы загрузить фрагмент кода для создания хранимой процедуры.

   ![список фрагментов кода](./media/tutorial-sql-editor/snippet-list.png)

3. Во фрагменте кода для создания хранимой процедуры есть два поля, которые можно быстро изменить: *StoredProcedureName* и *SchemaName*. Выберите поле *StoredProcedureName*, щелкните его правой кнопкой мыши и выберите пункт **Изменить все вхождения**. Теперь введите *getCustomer*, и все записи *StoredProcedureName* изменятся на *getCustomer*.

   ![фрагмент кода](./media/tutorial-sql-editor/snippet.png)

5. Измените все вхождения *SchemaName* на *dbo*. 
6. Фрагмент кода содержит параметры-заполнители и текст, которые нужно изменить. Инструкция *EXECUTE* также содержит текст-заполнитель, так как количество параметров процедуры изначально неизвестно. В целях этого руководства измените фрагмент кода, чтобы он выглядел так:

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
    
5. Чтобы создать хранимую процедуру и выполнить ее тестовый запуск, нажмите клавишу **F5**.

Хранимая процедура будет создана, и в области **Результаты** отобразятся сведения о клиенте в формате JSON. Чтобы увидеть отформатированные данные JSON, щелкните возвращенную запись. 


## <a name="use-peek-definition"></a>Использование функции "Показать определение" 

В [!INCLUDE[name-sos](../includes/name-sos-short.md)] есть возможность просмотреть определение объекта с помощью функции "Показать определение". В этом разделе создается еще одна хранимая процедура, а затем с помощью функции "Показать определение" определяются имеющиеся в таблице столбцы для быстрого создания тела этой процедуры.

1. Откройте новое окно редактора, нажав клавиши **CTRL+N**. 

2. Введите в редакторе строку *sql*, с помощью клавиши со стрелкой вниз перейдите к пункту *sqlCreateStoredProcedure* и нажмите клавишу *TAB* (или *ВВОД*), чтобы загрузить фрагмент кода для создания хранимой процедуры.
3. Введите значение *setCustomer* для поля *StoredProcedureName* и значение *dbo* для поля *SchemaName*.

3. Замените заполнители @param следующим определением:

   ```sql
   @json_val nvarchar(max)
   ```

4. Замените тело хранимой процедуры следующим кодом:
   ```sql
   INSERT INTO dbo.Customers
   ```

5. В добавленной строке *INSERT* щелкните правой кнопкой мыши элемент **dbo.Customers** и выберите пункт **Показать определение**.

   ![показать определение](./media/tutorial-sql-editor/peek-definition.png)

6. Появится определение таблицы, из которого можно быстро понять, какие столбцы имеются в таблице. Используйте список столбцов, чтобы легко заполнить инструкции для хранимой процедуры. Завершите создание ранее добавленной инструкции INSERT, чтобы полностью подготовить тело хранимой процедуры, а затем закройте окно "Показать определение".

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
7. Удалите (или закомментируйте) команду *EXECUTE* в конце запроса.
8. Инструкция в итоге должна выглядеть так:

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

8. Чтобы создать хранимую процедуру *setCustomer*, нажмите клавишу **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Сохранение результатов запроса в формате JSON для тестирования хранимой процедуры setCustomer

Хранимая процедура *setCustomer*, созданная в предыдущем разделе, требует передачи данных JSON в параметр *\@json_val*. В этом разделе показано, как получить правильно отформатированные данные JSON для передачи в параметре, чтобы можно было протестировать хранимую процедуру.

1. На боковой панели **Серверы** щелкните правой кнопкой мыши таблицу *dbo.Customers* и выберите пункт **Выбрать первые 1000 строк**.

2. Выберите первую строку в представлении результатов (чтобы выделить всю строку, щелкните номер 1 в самом левом столбце), а затем выберите команду **Сохранить в формате JSON**.  
3. Выберите папку, которую легко запомнить, чтобы можно было удалить файл позднее (например, рабочий стол), и нажмите кнопку **Сохранить**. Откроется файл в формате JSON.

   ![сохранение в формате JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Выделите в редакторе данные JSON и скопируйте их.
5. Откройте новое окно редактора, нажав клавиши **CTRL+N**.
6. В предыдущих шагах было показано, как можно легко получить правильно отформатированные данные для выполнения вызова процедуры *setCustomer*. В приведенном ниже коде аналогичный формат JSON применяется к новым сведениям о клиенте для тестирования процедуры *setCustomer*. Инструкция включает в себя синтаксические конструкции для объявления параметра и выполнения новых процедур получения и задания. Вы можете скопировать данные из предыдущего раздела, вставить их, а затем изменить в соответствии с приведенным ниже примером либо просто вставить приведенную ниже инструкцию в редактор запросов.

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

7. Чтобы выполнить скрипт, нажмите клавишу **F5**. Этот скрипт вставляет данные нового клиента, а затем возвращает их в формате JSON. Щелкните результат, чтобы открыть отформатированное представление.

   ![результат теста](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Дальнейшие действия
В этом руководстве вы узнали, как выполнять следующие задачи:
> [!div class="checklist"]
> * быстрый поиск объектов схемы;
> * изменение данных таблицы; 
> * написание скрипта T-SQL с помощью фрагментов кода;
> * получение сведений об объектах базы данных с помощью функций "Показать определение" и "Перейти к определению".


Чтобы узнать, как включить мини-приложение **Пять самых медленных запросов**, выполните следующее руководство:

> [!div class="nextstepaction"]
> [Включение примера аналитического мини-приложения для просмотра медленных запросов](tutorial-qds-sql-server.md)
