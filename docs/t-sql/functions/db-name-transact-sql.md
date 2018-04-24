---
title: DB_NAME (Transact-SQL) | Документы Майкрософт
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7f9a0898e617c5bc5b4680ce839e3ffa9ef15132
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="dbname-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает имя базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*database_id*  
Идентификатор возвращаемой базы данных. Аргумент *database_id* имеет тип **int** и не имеет значения по умолчанию. Если идентификационный номер не указан, возвращается имя текущей базы данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
**nvarchar(128)**
  
## <a name="permissions"></a>Разрешения  
Если участник, вызывающий **DB_NAME**, не является владельцем базы данных, а база данных не является базой данных **master** или **tempdb**, минимально необходимыми разрешениями для просмотра соответствующей строки являются разрешения уровня сервера ALTER ANY DATABASE или VIEW ANY DATABASE либо разрешение CREATE DATABASE для базы данных **master**. Узнать базу данных, к которой подключен участник, можно в представлении каталога **sys.databases**.
  
> [!IMPORTANT]  
>  По умолчанию общедоступная роль имеет разрешение VIEW ANY DATABASE, что позволяет всем именам для входа просматривать информацию в базе данных. Чтобы лишить имя для входа возможности обнаруживать базу данных, отзовите общедоступное разрешение VIEW ANY DATABASE с помощью инструкции REVOKE или отмените разрешение VIEW ANY DATABASE для отдельных имен для входа с помощью инструкции DENY.  
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>В. Получение имени текущей базы данных  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>Г. Получение имени базы данных по ее идентификатору  
В приведенном ниже примере возвращается имя и идентификатор каждой базы данных.
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>См. также раздел
[DB_ID (Transact-SQL)](../../t-sql/functions/db-id-transact-sql.md)  
[Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  

