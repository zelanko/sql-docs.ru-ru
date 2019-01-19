---
title: Использование функции EVENTDATA | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- EVENTDATA function
- DDL triggers, EVENTDATA function
ms.assetid: 675b8320-9c73-4526-bd2f-91ba42c1b604
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a34a3e69e157894b29db48da19f44d1e35dad746
ms.sourcegitcommit: 2e8783e6bedd9597207180941be978f65c2c2a2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2019
ms.locfileid: "54405684"
---
# <a name="use-the-eventdata-function"></a>Использование функции EVENTDATA
  Функция EVENTDATA позволяет получить сведения о событии, которое привело к срабатыванию триггера DDL. Эта функция возвращает значение типа `xml`. XML-схема содержит следующие сведения:  
  
-   время формирования события;  
  
-   идентификатор системного процесса (SPID), соответствующий соединению, во время которого был выполнен триггер;  
  
-   тип события, которое привело к срабатыванию триггера.  
  
 В зависимости от типа события эта схема включает также дополнительные сведения о базе данных, в которой было сформировано событие, об объекте, в контексте которого оно было сформировано, и об инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , вызвавшей это событие. Дополнительные сведения см. в разделе [DDL Triggers](ddl-triggers.md).  
  
 Предположим, что в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] создан следующий триггер DDL:  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
```  
  
 После этого выполняется следующая инструкция `CREATE TABLE` :  
  
 `CREATE TABLE NewTable (Column1 int);`  
  
 Инструкция `EVENTDATA()` в триггере DDL захватывает текст инструкции `CREATE TABLE` , что является недопустимым. Это достигается с помощью инструкции XQuery, применяемой `xml` , порожденным функцией EVENTDATA и получения \<CommandText > элемента. Дополнительные сведения см. в статье [Справочник по языку XQuery (SQL Server)](/sql/xquery/xquery-language-reference-sql-server).  
  
> [!CAUTION]  
>  Функция EVENTDATA захватывает данные событий CREATE_SCHEMA, а также элемента <schema_element> соответствующего определения CREATE SCHEMA, если таковые существуют. Кроме этого, функция EVENTDATA распознает определение <schema_element> как отдельное событие. Таким образом, триггер DDL, созданный для события CREATE_SCHEMA и для события, представленного данными <schema_element> определения CREATE SCHEMA, может дважды вернуть одни и те же сведения о событии (например, данные `TSQLCommand`). Допустим, для событий CREATE_SCHEMA и CREATE_TABLE создан триггер DDL и выполняется следующий пакет:  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  Если приложение использует данные `TSQLCommand` о событии CREATE_TABLE, следует учитывать, что эти данные могут появиться дважды: при возникновении события CREATE_SCHEMA и при возникновении события CREATE_TABLE. Следует избегать создания триггеров DDL одновременно для событий CREATE_SCHEMA и текста <schema_element> для любых соответствующих определений CREATE SCHEMA, или же в приложение необходимо добавить элемент логики, чтобы одно и тоже событие не обрабатывалось дважды.  
  
## <a name="alter-table-and-alter-database-events"></a>События ALTER TABLE и ALTER DATABASE  
 Данные о событиях  для событий ALTER_TABLE и ALTER_DATABASE также включают имена и типы других объектов, затронутых DDL-инструкцией и действием, выполняемым над этими объектами. Данные события ALTER_TABLE включают имена столбцов, ограничений или триггеров, затронутых инструкцией ALTER TABLE и действием (создание, изменение, удаление, включение или отключение), выполняемым над затронутыми объектами. Данные события ALTER_DATABASE включают имена любых файлов или файловых групп, затронутых инструкцией ALTER DATABASE и действием (создание, изменение, удаление), выполняемым над затронутыми объектами.  
  
 Предположим, что в образце базы данных AdventureWorks создан следующий триггер DDL:  
  
```  
CREATE TRIGGER ColumnChanges  
ON DATABASE   
FOR ALTER_TABLE  
AS  
-- Detect whether a column was created/altered/dropped.  
SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]', 'nvarchar(max)')  
RAISERROR ('Table schema cannot be modified in this database.', 16, 1);  
ROLLBACK;  
```  
  
 Затем выполняется следующая инструкция ALTER TABLE, нарушающая ограничение:  
  
```  
ALTER TABLE Person.Address ALTER COLUMN ModifiedDate date;   
```  
  
 Инструкция EVENTDATA() в триггере DDL захватывает текст инструкции `ALTER TABLE` , что является недопустимым.  
  
## <a name="example"></a>Пример  
 Функция EVENTDATA может применяться для создания журнала событий. В следующем примере создается таблица для хранения информации о событиях. После этого для текущей базы данных создается триггер DDL, который при любом событии DDL уровня базы данных заполняет эту таблицу следующими данными:  
  
-   время формирования события (функция GETDATE);  
  
-   пользователь базы данных, инициировавший сеанс, во время которого произошло событие (функция CURRENT_USER);  
  
-   тип события;  
  
-   инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] , вызвавшая данное событие.  
  
 Сведения о двух последних элементах регистрируются путем выполнения запроса XQuery для `xml`-данных, сформированных функцией EVENTDATA.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger  
CREATE TABLE TestTable (a int)  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
```  
  
> [!NOTE]  
>  Для получения сведения о событиях в запросе XQuery вместо метода `value()` рекомендуется использовать метод `query()`. Метод `query()` возвращает XML-данные и символы возврата каретки и переноса строки, заэкранированные амперсандом, тогда как в выводе метода `value()` эти символы не экранируются.  
  
 Аналогичный пример триггера DDL предоставляется вместе с образцом базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Для его получения перейдите в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в папку с триггерами базы данных, Эта папка находится в папке **Programmability** базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Щелкните правой кнопкой мыши **ddlDatabaseTriggerLog** и выберите **создать скрипт для триггера базы данных**. По умолчанию триггер DDL **ddlDatabaseTriggerLog** отключена.  
  
## <a name="see-also"></a>См. также  
 [DDL-события](../triggers/ddl-events.md)   
 [Группы DDL-событий](../triggers/ddl-event-groups.md)  
  
  
