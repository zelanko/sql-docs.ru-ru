---
title: "DROP TRIGGER (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TRIGGER
- DROP_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- renaming triggers
- triggers [SQL Server], removing
- DDL triggers, removing
- DROP TRIGGER statement
- deleting triggers
- dropping triggers
- removing triggers
- DML triggers, removing
ms.assetid: 092d0d71-9f1e-4e38-a1c4-2487adfa5b4e
caps.latest.revision: 53
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3ca35b2b33a60d0af5dd31467f1381402f8f99b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-trigger-transact-sql"></a>DROP TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет один или более триггеров DML или DDL из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
DROP TRIGGER [ IF EXISTS ] [schema_name.]trigger_name [ ,...n ] [ ; ]  
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE statement (DDL Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON { DATABASE | ALL SERVER }   
[ ; ]  
  
-- Trigger on a LOGON event (Logon Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON ALL SERVER  
```  

  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658), [!INCLUDE[sssds](../../includes/sssds-md.md)]).  
  
 Условно Удаляет триггер только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит триггер DML. Действие триггеров DML ограничивается областью схемы таблицы или представления, для которых они созданы. *schema_name* не может быть указан для триггеров DDL или входа.  
  
 *имя_триггера*  
 Имя удаляемого триггера. Чтобы просмотреть список созданных триггеров, используйте [sys.server_assembly_modules](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) или [sys.server_triggers](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
 DATABASE  
 Обозначает область действия триггера DDL в текущей базе данных. Если при создании или изменении триггера был указан аргумент DATABASE, то он должен указываться и далее.  
  
 ALL SERVER  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Обозначает область действия триггера DDL на текущем сервере. Если при создании или изменении триггера был указан аргумент ALL SERVER, то он должен указываться и далее. Параметр ALL SERVER также применяется к триггерам входа.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
## <a name="remarks"></a>Замечания  
 Триггер DML может быть удален напрямую или в результате удаления таблицы триггера. При удалении таблицы удаляются все связанные с ней триггеры.  
  
 При удалении триггера, сведения о триггере удаляется из **sys.objects**, **sys.triggers** и **sys.sql_modules** представления каталога.  
  
 С помощью инструкции DROP TRIGGER сразу несколько триггеров DDL можно удалить только в том случае, если при их создании были использованы одинаковые предложения ON.  
  
 Чтобы переименовать триггер, используйте инструкции DROP TRIGGER и CREATE TRIGGER. Чтобы изменить определение триггера, используйте инструкцию ALTER TRIGGER.  
  
 Дополнительные сведения об определении зависимостей для конкретных триггеров см. в разделе [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md), [sys.dm_sql_referenced_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md), и [sys.dm_sql_referencing_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
 Дополнительные сведения о просмотре текста триггеров см. в разделе [sp_helptext &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md) и [sys.sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
 Дополнительные сведения о просмотре списка уже созданных триггеров см. в разделе [sys.triggers &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) и [sys.server_triggers &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Чтобы удалить триггер DML, необходимо разрешение ALTER для таблицы или представления, в которых определен данный триггер.  
  
 Чтобы удалить триггер входа или триггер DDL, определенный в области сервера (ON ALL SERVER), для этого сервера требуется разрешение CONTROL SERVER. Чтобы удалить триггер DDL, определенный в области базы данных (ON DATABASE), необходимо разрешение ALTER ANY DATABASE DDL TRIGGER для текущей базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-dml-trigger"></a>A. Удаление триггера DML  
 В следующем примере показано удаление триггера `employee_insupd` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. (Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] можно использовать синтаксис DROP TRIGGER IF EXISTS.)  
  
```  
IF OBJECT_ID ('employee_insupd', 'TR') IS NOT NULL  
   DROP TRIGGER employee_insupd;  
```  
  
### <a name="b-dropping-a-ddl-trigger"></a>Б. Удаление триггера DDL  
 В ходе выполнения следующего примера происходит удаление триггера DDL `safety`.  
  
> [!IMPORTANT]  
>  Так как триггеры DDL не ограничены областью схемы и поэтому не отображаются в **sys.objects** представление каталога функция OBJECT_ID не может использоваться для выяснения факта существования базы данных. Запросы на объекты, не относящиеся к области схемы, должны выполняться при помощи соответствующих представлений каталогов. Триггеры DDL, используйте **sys.triggers**.  
  
```  
DROP TRIGGER safety  
ON DATABASE;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ENABLE TRIGGER (Transact-SQL)](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER (Transact-SQL)](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Получение сведений о триггерах DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  

