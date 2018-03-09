---
title: "DISABLE TRIGGER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISABLE_TSQL
- DISABLE
- DISABLE TRIGGER
- DISABLE_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DML triggers, disabling
- DDL triggers, disabling
- DISABLE TRIGGER statement
- triggers [SQL Server], disabling
- disabling triggers
ms.assetid: e6529f06-e442-437e-a7bf-41790bc092c5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 69398e740c4ae5ca49c93b1f70d7c02a0d3fbf42
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="disable-trigger-transact-sql"></a>DISABLE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отключает триггер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DISABLE TRIGGER { [ schema_name . ] trigger_name [ ,...n ] | ALL }  
ON { object_name | DATABASE | ALL SERVER } [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы, к которой принадлежит триггер. *schema_name* не может быть указан для триггеров DDL или входа.  
  
 *имя_триггера*  
 Имя триггера, который нужно отключить.  
  
 ALL  
 Означает, что все триггеры в области действия предложения ON будут отключены.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает триггеры в базах данных, опубликованных для репликации слиянием. Если в опубликованных базах данных указано значение ALL, то эти триггеры отключаются, что прерывает репликацию. Перед тем как задавать значение ALL, убедитесь, что текущая база данных не опубликована для репликации слиянием.  
  
 *object_name*  
 Имя таблицы или представления, на котором триггер DML *имя_триггера* был создан для выполнения.  
  
 DATABASE  
 Для триггера DDL показывает, что *имя_триггера* был создан или изменен для выполнения в области базы данных.  
  
 ALL SERVER  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Для триггера DDL показывает, что *имя_триггера* был создан или изменен для выполнения в области сервера. Параметр ALL SERVER также применяется к триггерам входа.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
## <a name="remarks"></a>Замечания  
 Триггеры включаются по умолчанию при создании. Отключение триггера не сбрасывает его. Триггер все еще существует как объект в текущей базе данных. Однако триггер не запускается, когда инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], для которых он запрограммирован, выполняются. Триггеры можно повторно включить с помощью [ENABLE TRIGGER](../../t-sql/statements/enable-trigger-transact-sql.md). Триггеры DML, определенные для таблиц можно также отключать и включать с помощью [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 Изменение триггера с помощью **ALTER TRIGGER** инструкция включает триггер.  
  
## <a name="permissions"></a>Permissions  
 Для отключения триггера DML пользователь должен обладать как минимум разрешением ALTER для таблицы или представления, где создан триггер.  
  
 Для отключения триггера DDL в области сервера (ON ALL SERVER) или триггера входа пользователь должен обладать разрешением CONTROL SERVER для этого сервера. Для отключения триггера DDL в области базы данных (ON DATABASE) пользователь должен обладать как минимум разрешением ALTER ANY DATABASE DDL TRIGGER в текущей базе данных.  
  
## <a name="examples"></a>Примеры  
Следующие примеры, описанные в базе данных AdventureWorks2012.
  
### <a name="a-disabling-a-dml-trigger-on-a-table"></a>A. Отключение триггера DML в таблице  
 В следующем примере показано отключение триггера `uAddress`, созданного для таблицы `Address`.  
  
```  
DISABLE TRIGGER Person.uAddress ON Person.Address;  
GO  
```  
  
### <a name="b-disabling-a-ddl-trigger"></a>Б. Отключение триггера DDL  
 В следующем примере создается триггер DDL `safety` в области базы данных, а затем он отключается.  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
GO  
DISABLE TRIGGER safety ON DATABASE;  
GO  
```  
  
### <a name="c-disabling-all-triggers-that-were-defined-with-the-same-scope"></a>В. Отключение всех триггеров, определенных в одной области  
 В следующем примере отключаются все триггеры DLL, созданные в области сервера.  
  
```  
DISABLE Trigger ALL ON ALL SERVER;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ENABLE TRIGGER (Transact-SQL)](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [sys.triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
  
