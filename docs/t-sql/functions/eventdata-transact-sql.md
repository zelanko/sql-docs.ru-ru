---
title: "EVENTDATA (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EVENTDATA
- fn_event_data
- EVENTDATA_TSQL
- fn_event_data_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server instance event data [SQL Server]
- event notifications [SQL Server], event status
- events [SQL Server], status infromation
- EVENTDATA function
- status information [SQL Server], events
- DDL triggers, returning event data
ms.assetid: 03a80e63-6f37-4b49-bf13-dc35cfe46c44
caps.latest.revision: 55
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b385ee993ab576307b6609670761deae9a7a1f6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о событиях сервера или базы данных. Функция EVENTDATA вызывается при уведомлении о событии, а результаты ее работы возвращаются указанному компоненту Service Broker. Кроме того, ее можно использовать в теле триггера DDL или триггера входа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>Замечания  
 Функция EVENTDATA возвращает данные только в том случае, если она вызвана непосредственно из триггера DDL или триггера входа. При вызове из других подпрограмм, даже вызванных триггером DDL или триггером входа, функция EVENTDATA возвращает значение NULL.  
  
 Данные, возвращенные функцией EVENTDATA, недействительны до тех пор, пока не будет выполнена явная или неявная фиксация или откат вызвавшей ее транзакции.  
  
> [!CAUTION]  
>  Функция EVENTDATA возвращает XML-данные. Эти данные отправляются клиенту в Юникоде, использующем 2 байта для представления каждого символа. XML-данные, возвращаемые функцией EVENTDATA, могут содержать следующие элементы Юникода.  
>   
>  `0x0009`  
>   
>  `0x000A`  
>   
>  `0x000D`  
>   
>  `>= 0x0020 && <= 0xD7FF`  
>   
>  `>= 0xE000 && <= 0xFFFD`  
>   
>  Некоторые символы, встречающиеся в идентификаторах и данных [!INCLUDE[tsql](../../includes/tsql-md.md)], не могут быть выражены в форме XML или не допускаются этим языком. Символы или данные с элементами кода, не указанными в приведенном выше списке, сопоставляются с вопросительным знаком (?).  
  
 Чтобы обеспечить безопасность имен входа, при выполнении инструкций CREATE LOGIN или ALTER LOGIN пароли не отображаются.  
  
## <a name="schemas-returned"></a>Возвращаемые схемы  
 Функция EVENTDATA возвращает значение типа **xml**. По умолчанию определение схемы для всех событий устанавливается в следующий каталог: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.  
  
 Кроме того, схема событий опубликована по [схемы XML Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkID=31850) веб-страницы.  
  
 Чтобы извлечь схему для какого-то конкретного события, нужно выполнить поиск в схеме для составного типа `EVENT_INSTANCE_\<event_type>`. Например, чтобы извлечь схему для события DROP_TABLE, выполните поиск в схеме для `EVENT_INSTANCE_DROP_TABLE`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. Запрос данных о событии в триггере DDL  
 В следующем примере создается триггер DDL для предотвращения создания новых таблиц в базе данных. Сведения об инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], активировавшей триггер, извлекаются с помощью запроса XQuery к XML-данным, сформированным функцией EVENTDATA. Дополнительные сведения см. в статье [Справочник по языку XQuery (SQL Server)](../../xquery/xquery-language-reference-sql-server.md).  
  
> [!NOTE]  
>  При выполнении запроса `\<TSQLCommand>` элемента с помощью **результаты в таблицу** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разрывы строк в тексте команды не отображаются. Используйте **в виде текста** вместо него.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value  
        ('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
GO  
--Test the trigger.  
CREATE TABLE NewTable (Column1 int);  
GO  
--Drop the trigger.  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
> [!NOTE]  
>  Если требуется возвратить данные о событиях, рекомендуется использовать метод XQuery **value()** вместо метода **query()** метод. **Query()** метод возвращает XML и escape-знак возврата каретки и перевода строки (CR/LF) экземпляров в выходных данных, пока **value()** отображает CR/LF в выводе.  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>Б. Создание таблицы журнала с данными о событии в триггере DDL  
 В следующем примере создается таблица для хранения сведений обо всех событиях уровня базы данных, которая заполняется триггером DDL. Тип события и инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] извлекаются с помощью запроса XQuery к XML-данным, сформированным функцией `EVENTDATA`.  
  
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
--Test the trigger.  
CREATE TABLE TestTable (a int);  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
--Drop the trigger.  
DROP TRIGGER log  
ON DATABASE;  
GO  
--Drop table ddl_log.  
DROP TABLE ddl_log;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование функции EVENTDATA](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [Триггеры DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [Уведомления о событиях](../../relational-databases/service-broker/event-notifications.md)   
 [Триггеры входа](../../relational-databases/triggers/logon-triggers.md)  
  
  

