---
title: "DB_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_ID_TSQL
- DB_ID
dev_langs:
- TSQL
helpviewer_keywords:
- viewing database ID numbers
- IDs [SQL Server], databases
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
- displaying database ID numbers
- DB_ID function
ms.assetid: 7b3aef89-a6fd-4144-b468-bf87ebf381b8
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 30d34b3509517d18559d4fbb0aa02a92e6d6cfe8
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="dbid-transact-sql"></a>DB_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает идентификационный номер базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DB_ID ( [ 'database_name' ] )   
```  
  
## <a name="arguments"></a>Аргументы  
"*имя_базы_данных*"  
Имя базы данных, используемое для возврата соответствующего идентификатора базы данных. *database_name* — **sysname**. Если *имя_базы_данных* будет пропущен, возвращается идентификатор текущей базы данных.
  
## <a name="return-types"></a>Возвращаемые типы
**int**
  
## <a name="permissions"></a>Permissions  
Если код, вызывающий **DB_ID** не является владельцем базы данных и база данных не **master** или **tempdb**, являются минимальными разрешениями, необходимыми для просмотра соответствующей строки Разрешение уровня сервера ALTER ANY DATABASE или VIEW ANY DATABASE или разрешение CREATE DATABASE в **master** базы данных. Узнать базу данных, к которой подключен участник, можно в представлении каталога **sys.databases**.
  
> [!IMPORTANT]  
>  По умолчанию роли public имеет разрешение VIEW ANY DATABASE, что все имена входа просмотреть сведения о базе данных. Чтобы заблокировать вход с возможность обнаружения базы данных, ОТМЕНИТЬ разрешение VIEW ANY DATABASE с общедоступной или запретить разрешение VIEW ANY DATABASE для отдельных имен входа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>A. Возвращение идентификатора текущей базы данных  
Следующий пример демонстрирует возврат идентификатора текущей базы данных.
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>Б. Возвращение идентификатора указанной базы данных  
В следующем примере возвращается идентификатор базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных.
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-dbid-to-specify-the-value-of-a-system-function-parameter"></a>В. Использование DB_ID для указания значения параметра системной функции  
В следующем примере используется `DB_ID` для возврата идентификатора [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных в системной функции `sys.dm_db_index_operational_stats`. Эта функция принимает идентификатор базы данных в качестве первого параметра.
  
```sql
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>Г. Возвращает идентификатор текущей базы данных  
Следующий пример демонстрирует возврат идентификатора текущей базы данных.
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>Д. Возвращает идентификатор указанной базы данных.  
Следующий пример возвращает идентификатор базы данных из базы данных AdventureWorksDW2012.
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>См. также:
[Db_name &#40; Transact-SQL &#41;](../../t-sql/functions/db-name-transact-sql.md)  
[Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  


