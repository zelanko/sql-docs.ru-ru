---
title: "Триггеры DDL | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-ddl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DDL triggers, about DDL triggers
ms.assetid: 1a4a6564-9820-4a14-9305-2c0e9ea37454
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ebc22f2c34fbfa6e45874ee90cfb1fd8344e5c31
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="ddl-triggers"></a>Триггеры DDL
  Триггеры DDL активируются в ответ на различные события языка DDL. Эти события в основном соответствуют инструкциям [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые начинаются с ключевых слов CREATE, ALTER, DROP, GRANT, DENY, REVOKE или UPDATE STATISTICS. Системные хранимые процедуры, выполняющие операции, подобные операциям DDL, также могут запускать триггеры DDL.  
  
 Используйте триггеры DDL, если хотите сделать следующее.  
  
-   Предотвращать внесение определенных изменений в схему базы данных.  
  
-   Настроить выполнение в базе данных некоторых действий в ответ на изменения в схеме базы данных.  
  
-   Записывать изменения или события схемы базы данных.  
  
> [!IMPORTANT]  
>  Тестировать триггеры DDL, чтобы определить, как они отвечают на запущенные системные хранимые процедуры. Например: как инструкция CREATE TYPE, так и хранимая процедура **sp_addtype** вызывают срабатывание триггера DDL, созданного на событии CREATE_TYPE.  
  
## <a name="types-of-ddl-triggers"></a>Типы триггеров DDL  
 Триггер DDL языка Transact-SQL  
 Хранимая процедура [!INCLUDE[tsql](../../includes/tsql-md.md)] особого типа, которая выполняет одну или несколько инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] в ответ на событие из области действия сервера или базы данных. Например, триггер DDL может активироваться, если выполняется такая инструкция, как ALTER SERVER CONFIGURATION, или если происходит удаление таблицы с использованием команды DROP TABLE.  
  
 Триггер DDL среды CLR  
 Вместо вызова хранимой процедуры на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] триггер CLR вызывает один или несколько методов управляемого кода, являющихся членами сборки, созданной с помощью среды .NET Framework и загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Триггеры DDL срабатывают только после выполнения соответствующих инструкций DDL. Триггеры DDL нельзя использовать в качестве триггеров INSTEAD OF. Триггеры DDL не срабатывают в ответ на события, влияющие на локальные или глобальные временные таблицы и хранимые процедуры.  
  
 Триггеры DDL не создают специальные таблицы **inserted** и **deleted** .  
  
 Сведения о событии, приведшем к срабатыванию триггера DDL, и последующих изменениях, выполненных триггером, можно получить при помощи функции EVENTDATA.  
  
 Для каждого события DDL должно быть создано несколько триггеров.  
  
 В отличие от триггеров DML, триггеры DDL не ограничены областью схемы. Поэтому для запроса метаданных о триггерах DDL нельзя воспользоваться такими функциями как OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY и OBJECTPROPERTYEX. Используйте вместо них представления каталога.  
  
 Триггеры DDL сервера появляются в обозревателе объектов среды SQL Server Management Studio в папке **Triggers** . Эта папка находится под папкой **Объекты сервера** . Триггеры DDL, доступные в области базы данных, находятся в папке **Триггеры базы данных** . Эта папка находится в папке **Программирование** соответствующей базы данных.  
  
> [!IMPORTANT]  
>  Вредоносный программный код внутри триггеров может быть запущен с расширенными правами доступа. Дополнительные сведения о том, как уменьшить эту угрозу, см. в статье [Управление безопасностью триггеров](../../relational-databases/triggers/manage-trigger-security.md).  
  
## <a name="ddl-trigger-scope"></a>Область действия триггера DDL  
 Триггеры DLL срабатывают в ответ на событие [!INCLUDE[tsql](../../includes/tsql-md.md)] , обработанное текущей базой данных или текущим сервером. Область триггера зависит от события. Например, триггер DDL, созданный для срабатывания на событие CREATE TABLE, может срабатывать каждый раз, когда в базе данных или в экземпляре сервера возникает событие CREATE_TABLE. Триггер DDL, созданный для запуска в ответ на событие CREATE_LOGIN, может выполнять это только при возникновении события CREATE_LOGIN в экземпляре сервера.  
  
 В следующем примере триггер DDL `safety` будет срабатывать каждый раз, когда в базе данных будет выполняться инструкция `DROP_TABLE` или происходить событие `ALTER_TABLE` .  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
```  
  
 В следующем примере триггер DDL выводит сообщение, если в текущем экземпляре сервера происходит любое событие `CREATE_DATABASE` . В этом примере используется функция `EVENTDATA` для получения текста соответствующей инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Дополнительные сведения об использовании EVENTDATA с триггерами DDL см. в статье [Использование функции EVENTDATA](../../relational-databases/triggers/use-the-eventdata-function.md).  
  
```  
IF EXISTS (SELECT * FROM sys.server_triggers  
    WHERE name = 'ddl_trig_database')  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
  
```  
  
 Списки сопоставления инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] соответствующим областям можно найти по ссылкам в подразделе «Выбор определенной инструкции DDL для запуска триггера DDL» далее в этом разделе.  
  
 Триггеры DDL масштаба базы данных хранятся как объекты в базах данных, в которых они создаются. Триггеры DDL можно создавать и в базе данных **master** , и они будут работать точно так же, как триггеры, созданные в пользовательских базах данных. Чтобы получить сведения о триггерах DDL, можно послать запрос к представлению каталога **sys.triggers** . Запрос к **sys.triggers** можно выполнить в контексте базы данных, где были созданы триггеры. Или можно задать имя базы данных в качестве идентификатора, например **master.sys.triggers**.  
  
 Триггеры DDL масштаба триггера хранятся как объекты в базе данных **master** . Однако для получения сведений о триггерах DDL сервера можно направить запрос к представлению каталога **sys.server_triggers** в любом контексте базы данных.  
  
## <a name="specifying-a-transact-sql-statement-or-group-of-statements"></a>Определение инструкции или группы инструкций Transact-SQL  
  
### <a name="selecting-a-particular-ddl-statement-to-fire-a-ddl-trigger"></a>Выбор определенной инструкции DDL для запуска триггера DDL  
 Триггеры DDL могут срабатывать после выполнения одной или нескольких определенных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] . В предыдущем примере триггер `safety` срабатывает после любого события `DROP_TABLE` или `ALTER_TABLE` . Списки инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые можно задать для запуска триггера DDL, а также область действия триггера см. в статье [События DDL](../../relational-databases/triggers/ddl-events.md).  
  
### <a name="selecting-a-predefined-group-of-ddl-statements-to-fire-a-ddl-trigger"></a>Выбор предопределенной группы инструкций DDL для запуска триггера DDL  
 Триггер DDL может срабатывать после любого события [!INCLUDE[tsql](../../includes/tsql-md.md)] из заданной группы схожих событий. Например, если нужно, чтобы триггер DDL срабатывал после выполнения любой инструкции CREATE TABLE, ALTER TABLE или DROP TABLE, можно указать FOR DDL_TABLE_EVENTS в инструкции CREATE TRIGGER. После выполнения CREATE TRIGGER события, входящие в группу событий, добавляются в представление каталога **sys.trigger_events** .  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], если триггер создается для группы событий, представление **sys.trigger_events** не содержит сведения о группе событий. Представление **sys.trigger_events** содержит сведения только об отдельных событиях, входящих в группу. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий представление **sys.trigger_events** хранит метаданные о группе событий, для которой создан триггер, а также о событиях, входящих в эту группу. Поэтому в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях изменение событий, охваченных группами событий, не применяется к триггерам DDL, созданным в этих группах событий в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Список стандартных групп инструкций DDL для триггеров DDL, инструкции, входящие в эти группы событий, а также области, где можно программировать эти группы событий, приводятся в разделе [DDL Event Groups](../../relational-databases/triggers/ddl-event-groups.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Задача|Раздел|  
|----------|-----------|  
|Описывает, как создать, изменить, удалить или отключить триггеры DDL.|[Реализация триггеров DDL](../../relational-databases/triggers/implement-ddl-triggers.md)|  
|Описывает, как создать триггер DDL CLR.|[Создание триггеров CLR](../../relational-databases/triggers/create-clr-triggers.md)|  
|Описывает, как возвратить сведения о триггерах DDL.|[Получение сведений о триггерах DDL](../../relational-databases/triggers/get-information-about-ddl-triggers.md)|  
|Описывает, как возвратить сведения о событии, которое активирует триггер DDL с использованием функции EVENTDATA.|[Использование функции EVENTDATA](../../relational-databases/triggers/use-the-eventdata-function.md)|  
|Описывает, как управлять безопасностью триггеров.|[Управление безопасностью триггеров](../../relational-databases/triggers/manage-trigger-security.md)|  
  
## <a name="see-also"></a>См. также:  
 [Триггеры DML](../../relational-databases/triggers/dml-triggers.md)   
 [Триггеры входа](../../relational-databases/triggers/logon-triggers.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
