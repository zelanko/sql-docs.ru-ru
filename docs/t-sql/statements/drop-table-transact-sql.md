---
title: "DROP TABLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/12/2017
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
- DROP_TABLE_TSQL
- DROP TABLE
dev_langs:
- TSQL
helpviewer_keywords:
- removing indexes
- table removal [SQL Server]
- deleting indexes
- dropping data
- deleting tables
- dropping indexes
- removing constraints
- removing permissions
- DROP TABLE statement
- removing tables
- deleting triggers
- removing data
- dropping tables
- deleting permissions
- dropping triggers
- deleting constraints
- removing triggers
- deleting data
- dropping constraints
- dropping permissions
ms.assetid: 0b6f2b6f-3aa3-4767-943f-43df3c3c5cfd
caps.latest.revision: 61
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22fa2a1da83dfef0743c089256fcd1e18af9b54c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-table-transact-sql"></a>DROP TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет одно или больше определений таблиц и все данные, индексы, триггеры, ограничения и разрешения для этих таблиц. Любое представление или хранимая процедура, ссылающаяся на удаленную таблицу должно быть явно удалена с помощью [DROP VIEW](../../t-sql/statements/drop-view-transact-sql.md) или [DROP PROCEDURE](../../t-sql/statements/drop-procedure-transact-sql.md). Отчет о зависимостях в таблице, используйте [sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP TABLE [ IF EXISTS ] [ database_name . [ schema_name ] . | schema_name . ]  
table_name [ ,...n ]  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, в которой создана таблица.  
  
 База данных SQL Windows Azure поддерживает формат трехкомпонентного имени database_name.[schema_name].object_name, если database_name — это текущая база данных или database_name — это tempdb и object_name начинается с символа «#». База данных SQL Windows Azure не поддерживает четырехкомпонентные имена.  
  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляет таблицу только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица.  
  
 *имя_таблицы*  
 Имя таблицы, предназначенной для удаления.  
  
## <a name="remarks"></a>Замечания  
 Инструкцию DROP TABLE нельзя использовать для удаления таблицы, на которую ссылается ограничение FOREIGN KEY. Сначала следует удалить ссылающееся ограничение FOREIGN KEY или ссылающуюся таблицу. Если и ссылающаяся таблица, и таблица, содержащая первичный ключ, удаляются с помощью одной инструкции DROP TABLE, ссылающаяся таблица должна быть первой в списке.  
  
 Несколько таблиц можно удалить из любой базы данных. Если удаляемая таблица ссылается на первичный ключ другой таблицы, которая также удаляется, ссылающаяся таблица с внешним ключом должна стоять в списке перед таблицей, содержащей указанный первичный ключ.  
  
 При удалении таблицы относящиеся к ней правила и значения по умолчанию теряют привязку, а любые связанные с таблицей ограничения или триггеры автоматически удаляются. Если таблица будет создана заново, нужно будет заново привязать все правила и значения по умолчанию, заново создать триггеры и добавить необходимые ограничения.  
  
 При удалении всех строк в таблице с помощью инструкции DELETE *tablename* или с помощью инструкции TRUNCATE TABLE, таблица существует до своего удаления.  
  
 Большие таблицы и индексы, использующие более 128 экстентов, удаляются в два этапа: логически и физически. На логическом этапе существующие единицы распределения, используемые в таблице, отмечаются для освобождения и остаются заблокированными до фиксации транзакции. В физической фазе IAM-страницы, помеченные для освобождения, физически удаляются пакетами.  
  
 При удалении таблицы, которая содержит столбец VARBINARY(MAX) с атрибутом FILESTREAM, не будут удалены никакие данные, которые хранятся в файловой системе.  
  
> [!IMPORTANT]  
>  Инструкции DROP TABLE и CREATE TABLE нельзя выполнять для одной таблицы в одном пакете. В противном случае может произойти непредвиденная ошибка.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER на схему, к которой принадлежит эта таблица, разрешение CONTROL для этой таблицы или членство в предопределенной роли базы данных **db_ddladmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-table-in-the-current-database"></a>A. Удаление таблицы из текущей базы данных  
 Следующий пример удаляет таблицу `ProductVendor1`, ее данные и индексы из текущей базы данных.  
  
```  
DROP TABLE ProductVendor1 ;  
```  
  
### <a name="b-dropping-a-table-in-another-database"></a>Б. Удаление таблицы из другой базы данных  
 Следующий пример удаляет таблицу `SalesPerson2` из базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Пример может быть выполнен из любой базы данных на экземпляре сервера.  
  
```  
DROP TABLE AdventureWorks2012.dbo.SalesPerson2 ;  
```  
  
### <a name="c-dropping-a-temporary-table"></a>В. Удаление временной таблицы  
 Следующий пример создает временную таблицу, проверяет ее наличие, удаляет ее и снова проверяет ее наличие. В этом примере не использует **IF EXISTS** синтаксис, который доступен, начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
CREATE TABLE #temptable (col1 int);  
GO  
INSERT INTO #temptable  
VALUES (10);  
GO  
SELECT * FROM #temptable;  
GO  
IF OBJECT_ID(N'tempdb..#temptable', N'U') IS NOT NULL   
DROP TABLE #temptable;  
GO  
--Test the drop.  
SELECT * FROM #temptable;  
  
```  
  
### <a name="d-dropping-a-table-using-if-exists"></a>Г. Удаление таблицы с помощью IF EXISTS  
  
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 В следующем примере создается таблица с именем T1. Затем вторая инструкция удаляет таблицу. Третья инструкция не выполняет никаких действий, так как таблица уже удалена, однако это не вызывает ошибку.  
  
```  
CREATE TABLE T1 (Col1 int);  
GO  
DROP TABLE IF EXISTS T1;  
GO  
DROP TABLE IF EXISTS T1;  
```  
  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [После УСЕЧЕНИЯ таблицы &#40; Transact-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)   
 [УДАЛИТЬ ПРЕДСТАВЛЕНИЕ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-view-transact-sql.md)   
 [DROP PROCEDURE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  

