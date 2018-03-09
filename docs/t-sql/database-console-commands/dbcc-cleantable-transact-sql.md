---
title: "Инструкция DBCC CLEANTABLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLEANTABLE_TSQL
- DBCC_CLEANTABLE_TSQL
- DBCC CLEANTABLE
- CLEANTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- disk space [SQL Server], reclaiming
- reclaiming space
- reallocating space
- removing columns
- DBCC CLEANTABLE statement
- space [SQL Server], reclaiming
- deleting columns
- dropping columns
ms.assetid: 0dbbc956-15b1-427b-812c-618a044d07fa
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dbc034e7ed5dd1d6f4704376adf73d517d3b5c47
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-cleantable-transact-sql"></a>DBCC CLEANTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]Освобождает место на диске из удаленных столбцов переменной длины в таблицы или индексированного представления.
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
  
DBCC CLEANTABLE  
(  
    { database_name | database_id | 0 }  
    , { table_name | table_id | view_name | view_id }  
    [ , batch_size ]  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* | *database_id* | 0  
 База данных, которой принадлежит очищаемая таблица. Если указано значение 0, используется текущая база данных. Имена баз данных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 *table_name* | *table_id* | *view_name*| *view_id*  
 Очищаемая таблица или индексированное представление.  
  
 *batch_size*  
 Число строк, которые обрабатываются за одну транзакцию. Если не указано или указано значение 0, инструкция обрабатывает всю таблицу за одну транзакцию.  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC CLEANTABLE освобождает место на диске после удаления столбца переменной длины. Столбец переменной длины может принимать одно из следующих типов данных: **varchar**, **nvarchar**, **varchar(max)**, **nvarchar(max)**, **varbinary**, **varbinary(max)**, **текст**, **ntext**, **изображения**,  **sql_variant**, и **xml**. Дисковое пространство после удаления столбца фиксированной длины не освобождается.
Если удаленные столбцы были сохранены в строке, инструкция DBCC CLEANTABLE освободит пространство из единицы распределения IN_ROW_DATA таблицы. Если столбцы были сохранены вне строк, пространство будет освобождено либо из единицы распределения ROW_OVERFLOW_DATA, либо из единицы распределения LOB_DATA, в зависимости от типа данных удаленного столбца. Если в результате освобождения пространства из страниц ROW_OVERFLOW_DATA или LOB_DATA была образована пустая страница, инструкция DBCC CLEANTABLE удалит эту страницу.
Инструкция DBCC CLEANTABLE выполняется за одну или несколько транзакций. Если не указан размер пакета, команда обрабатывает всю таблицу за одну транзакцию, при этом на время обработки производится ее монопольная блокировка. Для некоторых больших таблиц длительности транзакции и необходимого размера журнала может оказаться недостаточно. Если указан размер пакета, команда выполняет серию транзакций, в каждой из которых обрабатывается указанное число строк. Инструкция DBCC CLEANTABLE не может выполняться в транзакции, вложенной в другую транзакцию.
Эта операция выполняется с полной регистрацией.
Инструкция DBCC CLEANTABLE не поддерживается для использования с системными таблицами, временными таблицами и с частью таблицы, относящейся к индексу columnstore с оптимизацией для памяти xVelocity.
  
## <a name="best-practices"></a>Рекомендации  
Инструкция DBCC CLEANTABLE не должна выполняться как задача регламентного обслуживания. Вместо этого используйте инструкцию DBCC CLEANTABLE после выполнения значительных изменений над столбцами переменной длины в таблице или индексированном представлении, если необходимо незамедлительно освободить неиспользуемое пространство. Кроме того, можно выполнить перестроение индексов таблицы или представления, однако это более ресурсоемкая операция.
  
## <a name="result-sets"></a>Результирующие наборы  
Инструкция DBCC CLEANTABLE возвращает следующий результирующий набор.
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть владельцем таблицы или индексированного представления или быть членом **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных или **db_ddladmin** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
### <a name="a-using-dbcc-cleantable-to-reclaim-space"></a>A. Использование инструкции DBCC CLEANTABLE для освобождения дискового пространства  
В следующем примере выполняется инструкция DBCC CLEANTABLE для таблицы `Production.Document` в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql  
DBCC CLEANTABLE (AdventureWorks2012,'Production.Document', 0)  
WITH NO_INFOMSGS;  
GO  
```  
  
### <a name="b-using-dbcc-cleantable-and-verifying-results"></a>Б. Использование инструкции DBCC CLEANTABLE и проверка результатов  
В следующем примере создается таблица и заполняется несколькими столбцами переменной длины. Затем два столбца удаляются, а для освобождения неиспользуемого пространства выполняется инструкция DBCC CLEANTABLE. Запрос выполняется для проверки счетчиков страниц и пространства, используемого значениями до и после выполнения инструкции DBCC CLEANTABLE.
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('dbo.CleanTableTest', 'U') IS NOT NULL  
    DROP TABLE dbo.CleanTableTest;  
GO  
CREATE TABLE dbo.CleanTableTest  
    (FileName nvarchar(4000),   
    DocumentSummary nvarchar(max),  
    Document varbinary(max)  
    );  
GO  
-- Populate the table with data from the Production.Document table.  
INSERT INTO dbo.CleanTableTest  
    SELECT REPLICATE(FileName, 1000),   
           DocumentSummary,   
           Document  
    FROM Production.Document;  
GO  
-- Verify the current page counts and average space used in the dbo.CleanTableTest table.  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.CleanTableTest');  
SELECT alloc_unit_type_desc,   
       page_count,   
       avg_page_space_used_in_percent,   
       record_count  
FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'Detailed');  
GO  
-- Drop two variable-length columns from the table.  
ALTER TABLE dbo.CleanTableTest  
DROP COLUMN FileName, Document;  
GO  
-- Verify the page counts and average space used in the dbo.CleanTableTest table  
-- Notice that the values have not changed.  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.CleanTableTest');  
SELECT alloc_unit_type_desc,   
       page_count,   
       avg_page_space_used_in_percent,   
       record_count  
FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'Detailed');  
GO  
-- Run DBCC CLEANTABLE.  
DBCC CLEANTABLE (AdventureWorks2012,'dbo.CleanTableTest');  
GO  
-- Verify the values in the dbo.CleanTableTest table after the DBCC CLEANTABLE command.  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.CleanTableTest');  
SELECT alloc_unit_type_desc,   
       page_count,   
       avg_page_space_used_in_percent,   
       record_count  
FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'Detailed');  
GO  
```  
  
## <a name="see-also"></a>См. также  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
 [sys.allocation_units &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)  
  
  
