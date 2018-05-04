---
title: sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 6794e073-0895-4507-aba3-c3545acc843f
caps.latest.revision: 9
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6680957164eb494600fece4df5dddbae36ef4c0e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysfnstmtsqlhandlefromsqlstmt-transact-sql"></a>sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает **stmt_sql_handle** для [!INCLUDE[tsql](../../includes/tsql-md.md)] оператор в указанный тип параметризации (простую или принудительную). Это позволяет ссылаться на запросах, хранимых в хранилище запросов с помощью их **stmt_sql_handle** Если известен их текст.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.fn_stmt_sql_handle_from_sql_stmt   
(  
    'query_sql_text',   
    [ query_param_type   
) [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *query_sql_text*  
 — Текст запроса в хранилище запросов, требуется дескриптор. *query_sql_text* — **nvarchar(max)**, не имеет значения по умолчанию.  
  
 *query_param_type*  
 Представляет тип параметра запроса. *query_param_type* — **tinyint**. Возможны следующие значения:  
  
-   NULL — по умолчанию равно 0  
  
-   0 — нет  
  
-   1 — пользователя  
  
-   2 — простой  
  
-   3 — принудительно  
  
## <a name="columns-returned"></a>Возвращаемые столбцы  
 В следующей таблице перечислены столбцы, sys.fn_stmt_sql_handle_from_sql_stmt возвращает.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|**statement_sql_handle**|**varbinary(64)**|Дескриптор SQL.|  
|**query_sql_text**|**nvarchar(max)**|Текст [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.|  
|**query_parameterization_type**|**tinyint**|Тип параметризации запроса.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
  
## <a name="permissions"></a>Разрешения  
 Требуется **EXECUTE** разрешения в базе данных и **удалить** разрешения на представления каталога хранилища запросов.  
  
## <a name="examples"></a>Примеры  
 Следующий пример выполняет инструкцию, а затем использует `sys.fn_stmt_sql_handle_from_sql_stmt` чтобы возвращать дескриптор SQL этого оператора.  
  
```  
SELECT * FROM sys.databases;   
SELECT * FROM sys.fn_stmt_sql_handle_from_sql_stmt('SELECT * FROM sys.databases', NULL);  
```  
  
 Функция для согласования с другими динамическими административными представлениями данных в хранилище запросов. Следующий пример:  
  
```  
SELECT qt.query_text_id, q.query_id, qt.query_sql_text, qt.statement_sql_handle,  
q.context_settings_id, qs.statement_context_id   
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_id  
CROSS APPLY sys.fn_stmt_sql_handle_from_sql_stmt (qt.query_sql_text, null) AS fn_handle_from_stmt  
JOIN sys.dm_exec_query_stats AS qs   
    ON fn_handle_from_stmt.statement_sql_handle = qs.statement_sql_handle;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [Query Store Catalog Views (Transact-SQL) ](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  (Представления каталогов хранилища запросов (Transact-SQL))  
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
