---
title: "DROP VIEW (Transact-SQL) | Документы Майкрософт"
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
- DROP_VIEW_TSQL
- DROP VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- dropping views
- DROP VIEW statement
- deleting views
- indexed views [SQL Server], removing
- views [SQL Server], removing
- removing views
ms.assetid: 03cea355-e39c-46e1-b7db-8832038669dd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4ed2dc16e20179981985cc52812c8dbc44c0624b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-view-transact-sql"></a>DROP VIEW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет одно или несколько представлений из текущей базы данных. Инструкцию DROP VIEW можно выполнять для индексированных представлений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP VIEW [ IF EXISTS ] [ schema_name . ] view_name [ ...,n ] [ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP VIEW [ schema_name . ] view_name   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658), [!INCLUDE[sssds](../../includes/sssds-md.md)]).  
  
 Условное удаление представления только в том случае, если оно уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит представление.  
  
 *view_name*  
 Имя удаляемого представления.  
  
## <a name="remarks"></a>Примечания  
 При удалении представления из системного каталога удаляется его определение и другие сведения о нем. Все связанные с представлением разрешения также удаляются.  
  
 Любое представление таблицы, удаленной с помощью инструкции DROP TABLE, нужно удалять явно, с помощью инструкции DROP VIEW.  
  
 При применении инструкции DROP VIEW к индексированному представлению автоматически удаляются все индексы представления. Чтобы отобразить все индексы представления, используйте хранимую процедуру [sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
 При выполнении запросов к представлению компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет, существуют ли все указанные в инструкции объекты базы данных, правильны ли они в контексте инструкции и соответствуют ли инструкции, изменяющие данные, правилам обеспечения целостности данных. Если проверка завершается ошибкой, возвращается сообщение об ошибке. При успешной проверке операция преобразуется в операцию над базовой таблицей или таблицами. Если с момента создания представления изменились базовые таблицы или представления, может быть целесообразным удаление представления и его повторное создание.  
  
 Дополнительные сведения об определении зависимостей для конкретных представлений см. в разделе [sys.sql_dependencies](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md).  
  
 Дополнительные сведения о просмотре текста представления см. в разделе [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **CONTROL** на представление, разрешение **ALTER** на схему, содержащую представление, либо членство в предопределенной роли сервера **db_ddladmin**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-drop-a-view"></a>A. Удаление представления  
 В следующем примере удаляется представление `Reorder`.  
  
```  
DROP VIEW dbo.Reorder ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER VIEW (Transact-SQL)](../../t-sql/statements/alter-view-transact-sql.md)   
 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md)   
 [sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
 
