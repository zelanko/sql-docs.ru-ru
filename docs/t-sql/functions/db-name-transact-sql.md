---
title: "DB_NAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_NAME
- DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database names [SQL Server], DB_NAME
- names [SQL Server], databases
- viewing database names
- displaying database names
- DB_NAME function
ms.assetid: e21fb33a-a3ea-49b0-bb6b-8f789a675a0e
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5743ccb1374640078a77d84a140e9e5d0fdaef0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbname-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает имя базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*database_id*  
Идентификатор возвращаемой базы данных. *database_id* — **int**, не имеет значения по умолчанию. Если идентификационный номер не указан, возвращается имя текущей базы данных.
  
## <a name="return-types"></a>Возвращаемые типы
**nvarchar(128)**
  
## <a name="permissions"></a>Permissions  
Если код, вызывающий **DB_NAME** не является владельцем базы данных и база данных не **master** или **tempdb**, являются минимальными разрешениями, необходимыми для просмотра соответствующей строки Разрешение уровня сервера ALTER ANY DATABASE или VIEW ANY DATABASE или разрешение CREATE DATABASE в **master** базы данных. Узнать базу данных, к которой подключен участник, можно в представлении каталога **sys.databases**.
  
> [!IMPORTANT]  
>  По умолчанию роли public имеет разрешение VIEW ANY DATABASE, что все имена входа просмотреть сведения о базе данных. Чтобы заблокировать вход с возможность обнаружения базы данных, ОТМЕНИТЬ разрешение VIEW ANY DATABASE с общедоступной или запретить разрешение VIEW ANY DATABASE для отдельных имен входа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-current-database-name"></a>A. Возврат имени текущей базы данных  
Следующий пример возвращает имя текущей базы данных.
  
```sql
SELECT DB_NAME() AS [Current Database];  
GO  
```  
  
### <a name="b-returning-the-database-name-of-a-specified-database-id"></a>Б. Возврат имени базы данных с указанным идентификатором базы данных  
Следующий пример возвращает имя базы данных для идентификатора базы данных `3`.
  
```sql
USE master;  
GO  
SELECT DB_NAME(3)AS [Database Name];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>В. Возвращает имя текущей базы данных  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>Г. Возвращает имя базы данных, используя идентификатор базы данных  
Следующий пример возвращает имя базы данных и database_id для каждой базы данных.
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>См. также:
[DB_ID &#40; Transact-SQL &#41;](../../t-sql/functions/db-id-transact-sql.md)  
[Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  


