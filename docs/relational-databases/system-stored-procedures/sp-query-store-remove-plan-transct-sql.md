---
title: sp_query_store_remove_plan (Transct-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SP_QUERY_STORE_REMOVE_PLAN_TSQL
- SP_QUERY_STORE_REMOVE_PLAN_TSQL
- SP_QUERY_STORE_REMOVE_PLAN
- SYS.SP_QUERY_STORE_REMOVE_PLAN
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_remove_plan
- sp_query_store_remove_plan
ms.assetid: 88734726-135b-4b61-9f3f-f568c1fbece6
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ef04dee7a7384141aab820c2c65343a18b605ad0
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68418934"
---
# <a name="spquerystoreremoveplan-transct-sql"></a>sp_query_store_remove_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Удаляет один план из хранилища запросов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_query_store_remove_plan [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @plan_id = ] plan_id`Идентификатор удаляемого плана запроса. *plan_id* имеет тип **bigint**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **ALTER** на базу данных.
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о запросах в хранилище запросов.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Определив plan_id, который необходимо удалить, используйте следующий пример, чтобы удалить план запроса.  
  
```  
EXEC sp_query_store_remove_plan 3;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_query_store_force_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [Query Store Catalog Views (Transact-SQL) ](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  (Представления каталогов хранилища запросов (Transact-SQL))  
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
