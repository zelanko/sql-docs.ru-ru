---
title: "STATS_DATE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATS_DATE_TSQL
- STATS_DATE
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], last time updated
- STATS_DATE function
- query optimization statistics [SQL Server], last time updated
- last time statistics updated
ms.assetid: f9ec3101-1e41-489d-b519-496a0d6089fb
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 44fc7524040db874abc5d596b641cba985dcf893
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="statsdate-transact-sql"></a>STATS_DATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает дату последнего обновления статистики для таблицы или индексированного представления.  
  
 Дополнительные сведения об обновлении статистики см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STATS_DATE ( object_id , stats_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор таблицы или индексированного представления, содержащего статистику.  
  
 *stats_id*  
 Идентификатор объекта статистики.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает **datetime** в случае успешного выполнения. Возвращает **NULL** при возникновении ошибки.  
  
## <a name="remarks"></a>Замечания  
 Системные функции можно использовать в списке выбора, в предложении WHERE и в любом месте, где может быть использовано выражение.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner или разрешение на просмотр метаданных для таблицы или индексированного представления.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-the-dates-of-the-most-recent-statistics-for-a-table"></a>A. Возвращение даты последнего обновления статистики для таблицы  
 В следующем примере возвращается дата последнего обновления для каждого объекта статистики по таблице `Person.Address`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_update_date  
FROM sys.stats   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
 Если статистика соответствует индексу, *stats_id* значение в [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) представление каталога совпадает со значением *index_id* значение в [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) представление каталога, следующий запрос возвращает те же результаты, что и предыдущий запрос. Если статистика не соответствует индексу, то она будет содержаться в результатах sys.stats, но не в результатах sys.indexes.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-learn-when-a-named-statistics-was-last-updated"></a>Б. Дополнительные сведения, время последнего обновления статистики именованный  
 В следующем примере создается статистика по столбцу «Фамилия» в таблице DimCustomer. Затем выполняется запрос для отображения даты статистики. Затем он обновлений статистики и выполняет запрос еще раз, чтобы показать обновленными.  
  
```  
  
--First, create a statistics object  
USE AdventureWorksPDW2012;  
GO  
CREATE STATISTICS Customer_LastName_Stats  
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName)  
WITH SAMPLE 50 PERCENT;  
GO  
  
--Return the date when Customer_LastName_Stats was last updated  
USE AdventureWorksPDW2012;  
GO  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
--Update Customer_LastName_Stats so it will have a different timestamp in the next query  
GO  
UPDATE STATISTICS dbo.dimCustomer (Customer_LastName_Stats);  
  
--Return the date when Customer_LastName_Stats was last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
```  
  
### <a name="c-view-the-date-of-the-last-update-for-all-statistics-on-a-table"></a>В. Просмотр даты последнего обновления всей статистики для таблицы  
 Этот пример возвращает дату, время последнего обновления каждый объект статистики в таблице DimCustomer.  
  
```  
--Return the dates all statistics on the table were last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
 Если статистика соответствует индексу, *stats_id* значение в [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) представление каталога совпадает со значением *index_id* значение в [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) представление каталога, следующий запрос возвращает те же результаты, что и предыдущий запрос. Если статистика не соответствует индексу, то она будет содержаться в результатах sys.stats, но не в результатах sys.indexes.  
  
```  
USE AdventureWorksPDW2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [Статистика](../../relational-databases/statistics/statistics.md)  
  
  


