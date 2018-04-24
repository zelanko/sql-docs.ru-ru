---
title: DB_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 19cc0f913e68f0d3b602f27b5b427364c38d1b28
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
'*database_name*'  
Имя базы данных, используемое для возврата соответствующего идентификатора базы данных. Аргумент *database_name* имеет тип **sysname**. Если аргумент *database_name* не указан, возвращается идентификатор текущей базы данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
**int**
  
## <a name="permissions"></a>Разрешения  
Если участник, вызывающий **DB_ID**, не является владельцем базы данных, а база данных не является базой данных **master** или **tempdb**, минимально необходимыми разрешениями для просмотра соответствующей строки являются разрешения уровня сервера ALTER ANY DATABASE или VIEW ANY DATABASE либо разрешение CREATE DATABASE для базы данных **master**. Узнать базу данных, к которой подключен участник, можно в представлении каталога **sys.databases**.
  
> [!IMPORTANT]  
>  По умолчанию общедоступная роль имеет разрешение VIEW ANY DATABASE, что позволяет всем именам для входа просматривать информацию в базе данных. Чтобы лишить имя для входа возможности обнаруживать базу данных, отзовите общедоступное разрешение VIEW ANY DATABASE с помощью инструкции REVOKE или отмените разрешение VIEW ANY DATABASE для отдельных имен для входа с помощью инструкции DENY.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>A. Возвращение идентификатора текущей базы данных  
Следующий пример демонстрирует возврат идентификатора текущей базы данных.
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>Б. Возвращение идентификатора указанной базы данных  
В приведенном ниже примере возвращается идентификатор базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-dbid-to-specify-the-value-of-a-system-function-parameter"></a>В. Использование DB_ID для указания значения параметра системной функции  
В приведенном ниже примере `DB_ID` используется для получения идентификатора базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в системной функции `sys.dm_db_index_operational_stats`. Эта функция принимает идентификатор базы данных в качестве первого параметра.
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>Г. Получение идентификатора текущей базы данных  
Следующий пример демонстрирует возврат идентификатора текущей базы данных.
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>Д. Получение идентификатора именованной базы данных  
В приведенном ниже примере возвращается идентификатор базы данных AdventureWorksDW2012.
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>См. также раздел
[DB_NAME (Transact-SQL)](../../t-sql/functions/db-name-transact-sql.md)  
[Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  

