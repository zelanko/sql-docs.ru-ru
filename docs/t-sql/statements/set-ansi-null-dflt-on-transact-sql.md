---
title: "SET ANSI_NULL_DFLT_ON (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ANSI_NULL_DFLT_ON
- ANSI_NULL_DFLT_ON_TSQL
- SET ANSI_NULL_DFLT_ON
- SET_ANSI_NULL_DFLT_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULL_DFLT_ON statement
- ANSI_NULL_DFLT_ON option
- default nullability
- null values [SQL Server], overriding
- overriding default nullability
ms.assetid: 8c925924-a466-4c8b-aeb2-7e0d341f32db
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17bd1817d8f7f04401f49f9a02562bcf577c9088
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansinulldflton-transact-sql"></a>SET ANSI_NULL_DFLT_ON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет поведение сеанса, чтобы переопределить допустимость значений NULL по умолчанию для новых столбцов при **ANSI null по умолчанию** параметр базы данных имеет **false**. Дополнительные сведения об установке значения для **ANSI null по умолчанию**, в разделе [инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_NULL_DFLT_ON {ON | OFF}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULL_DFLT_ON ON;  
```  
  
## <a name="remarks"></a>Замечания  
 Данный параметр определяет допустимость значений NULL в новых столбцах только в случае, если допустимость значений NULL не указана в инструкциях CREATE TABLE и ALTER TABLE. Если значение SET ANSI_NULL_DFLT_ON равно ON, для новых, создаваемых с помощью инструкций ALTER TABLE и CREATE TABLE столбцов будут разрешены значения NULL, если для такого столбца явно не задана допустимость значений NULL. Параметр SET ANSI_NULL_DFLT_ON не влияет на столбцы, создаваемые с явным значением NULL или NOT NULL.  
  
 Оба параметра SET ANSI_NULL_DFLT_OFF и SET ANSI_NULL_DFLT_ON не могут быть установлены в ON одновременно. Если один параметр установлен в ON, то другой установлен в OFF. Поэтому можно установить в ON либо ANSI_NULL_DFLT_OFF, либо ANSI_NULL_DFLT_ON, или же установить оба параметра в OFF. Если один из параметров установлен в ON, применяется соответствующая установка (SET ANSI_NULL_DFLT_OFF или SET ANSI_NULL_DFLT_ON). Если оба параметра имеют значение OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение **is_ansi_null_default_on** столбца в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
 Для более надежного выполнения скриптов на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], используемых в базах данных с различными настройками допустимости значений NULL, лучше указывать свойства NULL или NOT NULL с помощью инструкций CREATE TABLE и ALTER TABLE.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_NULL_DFLT_ON автоматически устанавливается в значение ON при подключении. Значение SET ANSI_NULL_DFLT_ON для соединений из приложений DB-Library по умолчанию равно OFF.  
  
 Если значение SET ANSI_DEFAULTS равно ON, включается SET ANSI_NULL_DFLT_ON.  
  
 Параметр SET ANSI_NULL_DFLT_ON устанавливается во время выполнения или запуска, но не во время синтаксического анализа.  
  
 Настройка SET ANSI_NULL_DFLT_ON не используется при создании таблиц с помощью инструкции SELECT INTO.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @ANSI_NULL_DFLT_ON VARCHAR(3) = 'OFF';  
IF ( (1024 & @@OPTIONS) = 1024 ) SET @ANSI_NULL_DFLT_ON = 'ON';  
SELECT @ANSI_NULL_DFLT_ON AS ANSI_NULL_DFLT_ON;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано влияние `SET ANSI_NULL_DFLT_ON` с обеими настройками для **ANSI null по умолчанию** параметр базы данных.  
  
```  
USE AdventureWorks2012;  
GO  
  
-- The code from this point on demonstrates that SET ANSI_NULL_DFLT_ON  
-- has an effect when the 'ANSI null default' for the database is false.  
-- Set the 'ANSI null default' database option to false by executing  
-- ALTER DATABASE.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to ON and create table t2.  
SET ANSI_NULL_DFLT_ON ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL insert should succeed.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to OFF and create table t3.  
SET ANSI_NULL_DFLT_ON OFF;  
GO  
CREATE TABLE t3 (a TINYINT);  
GO  
-- NULL insert should fail.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- The code from this point on demonstrates that SET ANSI_NULL_DFLT_ON   
-- has no effect when the 'ANSI null default' for the database is true.  
-- Set the 'ANSI null default' database option to true.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON  
GO  
  
-- Create table t4.  
CREATE TABLE t4 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t4 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to ON and create table t5.  
SET ANSI_NULL_DFLT_ON ON;  
GO  
CREATE TABLE t5 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t5 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to OFF and create table t6.  
SET ANSI_NULL_DFLT_ON OFF;  
GO  
CREATE TABLE t6 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t6 (a) VALUES (NULL);  
GO  
  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1,t2,t3,t4,t5,t6;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SET ANSI_NULL_DFLT_OFF &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)  
  
  

