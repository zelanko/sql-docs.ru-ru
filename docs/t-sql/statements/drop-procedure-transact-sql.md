---
title: "DROP PROCEDURE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP PROCEDURE
- DROP_PROCEDURE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- removing stored procedures
- dropping procedure groups
- deleting stored procedures
- deleting procedure groups
- DROP PROCEDURE statement
- dropping stored procedures
- stored procedures [SQL Server], removing
- removing procedure groups
ms.assetid: 1c2d7235-7b9b-4336-8f17-429e7d82c2c3
caps.latest.revision: "51"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a154c40a9ede59d808d0ad77af685d27b23db208
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-procedure-transact-sql"></a>DROP PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет одну или несколько хранимых процедур или групп процедур из текущей базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP { PROC | PROCEDURE } [ IF EXISTS ] { [ schema_name. ] procedure } [ ,...n ]  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP { PROC | PROCEDURE } { [ schema_name. ] procedure_name }  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляет процедуру только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит процедура. Имя сервера или базы данных задавать нельзя.  
  
 *процедура*  
 Имя удаляемой хранимой процедуры или группы хранимых процедур. Нельзя удалить отдельные процедуры из группы пронумерованных процедур. Группа процедур удаляется полностью.  
  
## <a name="best-practices"></a>Рекомендации  
 Перед удалением хранимой процедуры проверьте зависимые объекты и измените эти объекты соответствующим образом. Удаление хранимой процедуры может вызвать сбой зависимых процедур и скриптов, если эти объекты не обновлены. Дополнительные сведения см. в разделе [Просмотр зависимостей хранимой процедуры](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)  
  
## <a name="metadata"></a>Метаданные  
 Для отображения списка существующих процедур, запросов **sys.objects** представления каталога. Чтобы просмотреть определения процедуры, запрос **sys.sql_modules** представления каталога.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуется **УПРАВЛЕНИЯ** разрешение на выполнение процедуры или **ALTER** разрешений на схему, которой принадлежит процедура, либо членство в **db_ddladmin** предопределенной роли сервера .  
  
## <a name="examples"></a>Примеры  
 В следующем примере хранимая процедура `dbo.uspMyProc` удаляется из текущей базы данных.  
  
```  
DROP PROCEDURE dbo.uspMyProc;  
GO  
```  
  
 В следующем примере из текущей базы данных удаляются несколько хранимых процедур.  
  
```  
DROP PROCEDURE dbo.uspGetSalesbyMonth, dbo.uspUpdateSalesQuotes, dbo.uspGetSalesByYear;  
```  
  
 В следующем примере удаляется `dbo.uspMyProc` хранимой процедуры, если он существует, но не приводят к ошибке, если процедура не существует. Этот синтаксис является новым в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
DROP PROCEDURE IF EXISTS dbo.uspMyProc;  
GO  
```  
  
  
## <a name="see-also"></a>См. также:  
 [ALTER PROCEDURE (Transact-SQL)](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Удаление хранимой процедуры](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)  
  
  


