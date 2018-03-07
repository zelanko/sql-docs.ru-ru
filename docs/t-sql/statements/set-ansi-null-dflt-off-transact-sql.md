---
title: "SET ANSI_NULL_DFLT_OFF (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/04/2017
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
f1_keywords:
- ANSI_NULL_DFLT_OFF_TSQL
- ANSI_NULL_DFLT_OFF
- SET ANSI_NULL_DFLT_OFF
- SET_ANSI_NULL_DFLT_OFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- default nullability
- ANSI_NULL_DFLT_OFF option
- null values [SQL Server], overriding
- overriding default nullability
- SET ANSI_NULL_DFLT_OFF statement
ms.assetid: 8ed5c512-f5de-4741-a18a-de85a3041295
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93677ffee0b86f342d07b8a129b6a1e0b2676d28
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="set-ansinulldfltoff-transact-sql"></a>SET ANSI_NULL_DFLT_OFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет поведение сеанса, чтобы переопределить допустимость значений NULL по умолчанию для новых столбцов, если параметр ANSI null по умолчанию для базы данных **true**. Дополнительные сведения об установке значения параметра ANSI null default см. в разделе [инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Синтаксис

```
-- Syntax for SQL Server and Azure SQL Database
  
SET ANSI_NULL_DFLT_OFF { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_NULL_DFLT_OFF OFF
```

## <a name="remarks"></a>Замечания  
 Данный параметр определяет допустимость значений NULL в новых столбцах только в случае, если допустимость значений NULL не указана в инструкциях CREATE TABLE и ALTER TABLE. Когда параметр SET ANSI_NULL_DFLT_OFF имеет значение ON, новые столбцы, создаваемые инструкциями ALTER TABLE и CREATE TABLE, по умолчанию принимают значение NOT NULL, если допустимость NULL в столбце явно не задана. Параметр SET ANSI_NULL_DFLT_OFF не влияет на столбцы, для которых при создании было явно указано значение NOT NULL или NULL.  
  
 Оба параметра SET ANSI_NULL_DFLT_OFF и SET ANSI_NULL_DFLT_ON не могут быть установлены в ON одновременно. Если один параметр установлен в ON, то другой установлен в OFF. Следовательно, только один из параметров — ANSI_NULL_DFLT_OFF или SET ANSI_NULL_DFLT_ON — может быть установлен в ON, или же оба могут быть установлены в OFF. Если один из параметров установлен в ON, применяется соответствующая установка (SET ANSI_NULL_DFLT_OFF или SET ANSI_NULL_DFLT_ON). Если оба параметра имеют значение OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение столбца is_ansi_null_default_on в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
 Для более надежной работы скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)], используемых в базах данных с различными настройками допустимости значений NULL, рекомендуется всегда указывать NULL или NOT NULL в инструкциях CREATE TABLE и ALTER TABLE.  
  
 Параметр настройки SET ANSI_NULL_DFLT_OFF устанавливается во время запуска или выполнения, но не во время синтаксического анализа.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @ANSI_NULL_DFLT_OFF VARCHAR(3) = 'OFF';  
IF ( (2048 & @@OPTIONS) = 2048 ) SET @ANSI_NULL_DFLT_OFF = 'ON';  
SELECT @ANSI_NULL_DFLT_OFF AS ANSI_NULL_DFLT_OFF;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует действие команды `SET ANSI_NULL_DFLT_OFF` с обеими настройками для параметра базы данных ANSI null default.  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Set the 'ANSI null default' database option to true by executing   
-- ALTER DATABASE.  
GO  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT);  
GO  
-- NULL INSERT should succeed.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t2.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL INSERT should fail.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t3.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t3 (a TINYINT) ;  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- This illustrates the effect of having both the database  
-- option and SET option disabled.  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t4.  
CREATE TABLE t4 (a tinyint) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t4 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t5.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t5 (a tinyint);  
GO   
-- NULL insert should fail.  
INSERT INTO t5 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t6.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t6 (a tinyint);   
GO   
-- NULL insert should fail.  
INSERT INTO t6 (a) VALUES (null);  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1, t2, t3, t4, t5, t6;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)  
  
  
