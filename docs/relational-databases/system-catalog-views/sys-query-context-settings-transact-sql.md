---
title: sys.query_context_settings (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/22/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- QUERY_CONTEXT_SETTINGS_TSQL
- SYS.QUERY_CONTEXT_SETTINGS_TSQL
- SYS.QUERY_CONTEXT_SETTINGS
- QUERY_CONTEXT_SETTINGS
dev_langs:
- TSQL
helpviewer_keywords:
- sys.query_context_settings catalog view
ms.assetid: 3c1887df-6bd8-491e-82fc-d25ad9589faf
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9be8b645cf0a5f08132110dd1eca43c19726d75a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysquerycontextsettings-transact-sql"></a>sys.query_context_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Содержит сведения о семантике, влияющие на параметры контекста, связанные с запросом. Существует ряд параметров контекста, доступных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , влияют на семантику запроса (определяя правильный результат запроса). Тот же текст запроса, который компилируется с различными настройками могут давать разные результаты (в зависимости от базовых данных).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**context_settings_id**|**bigint**|Первичный ключ. Это значение предоставляется в формате XML Showplan для запросов.|  
|**set_options**|**varbinary(8)**|Битовая маска, отражая состояние некоторые параметры SET. Дополнительные сведения см. в разделе [sys.dm_exec_plan_attributes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md).|  
|**language_id**|**smallint**|Идентификатор языка. Дополнительные сведения см. в разделе [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).|  
|**date_format**|**smallint**|Формат даты. Дополнительные сведения см. в разделе [SET DATEFORMAT (Transact-SQL)](../../t-sql/statements/set-dateformat-transact-sql.md).|  
|**date_first**|**tinyint**|Первое значение даты. Дополнительные сведения см. в разделе [SET DATEFIRST (Transact-SQL)](../../t-sql/statements/set-datefirst-transact-sql.md).|  
|**status**|**varbinary(2)**|Битовая маска, указывающая поле, которое указывает тип запроса или контекста, в котором был выполнен запрос. <br />Значение столбца может быть сочетанием несколько флагов (выраженного в шестнадцатеричном формате):<br /><br /> 0x0 — обычных запросов (определенные флаги не)<br /><br /> 0x1 — запрос, который был выполнен посредством одного из API-интерфейсы хранимые процедуры курсора<br /><br /> 0x2 — запроса на уведомление<br /><br /> 0x4 — внутреннего запроса<br /><br /> 0x8 — auto параметризованный запрос без универсальной параметризации<br /><br /> 0x10 — выборки курсора обновить запрос<br /><br /> 0x20 — запрос, используемый в запросы на обновление курсора<br /><br /> 0x40 - первоначальный результирующий набор возвращается, когда курсор открыт (Fetch курсор автоматически)<br /><br /> 0x80 – зашифрованные запроса<br /><br /> 0x100 — запроса в контексте предиката безопасности на уровне строки|  
|**required_cursor_options**|**int**|Параметры курсора, указанные пользователем, такие как тип курсора.|  
|**acceptable_cursor_options**|**int**|Параметры курсора, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может неявно преобразовывать для поддержания выполнения инструкции.|  
|**merge_action_type**|**smallint**|Тип плана выполнения триггера, используемого в результате **СЛИЯНИЯ** инструкции.<br /><br /> 0 указывает план без триггеров, план триггеров, который не выполняется в результате **СЛИЯНИЯ** инструкции или план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкцию, которая определяет только **Удалить** действие.<br /><br /> 1 означает **вставить** план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкции.<br /><br /> 2 указывает **обновление** план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкции.<br /><br /> 3 указывает **удаление** план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкции, содержащей соответствующий **вставить** или **обновление** действие.<br /><br /> <br /><br /> Наличие вложенных триггеров, выполняемых каскадными операциями, это значение является действием **СЛИЯНИЯ** инструкции, запустившей каскад.|  
|**default_schema_id**|**int**|Идентификатор схемы по умолчанию, который используется для разрешения имен, которые не являются полными.|  
|**is_replication_specific**|**бит**|Используется для репликации.|  
|**is_contained**|**varbinary(1)**|1 означает автономной базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW DATABASE STATE** разрешение.  
  
## <a name="see-also"></a>См. также  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Хранимые процедуры в хранилище запросов (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
