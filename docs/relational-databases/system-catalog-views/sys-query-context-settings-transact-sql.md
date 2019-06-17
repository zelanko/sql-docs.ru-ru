---
title: sys.query_context_settings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6c7ab77981c329c334b22d6fd9735188882b385c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013544"
---
# <a name="sysquerycontextsettings-transact-sql"></a>sys.query_context_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Содержит сведения о семантике, влияющие на параметры контекста, связанного с запросом. Существует ряд параметров контекста в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , влияют на семантику запроса (определяя правильный результат запроса). Тот же текст запроса, который компилируется в различных ситуациях может давать разные результаты (в зависимости от базовых данных).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**context_settings_id**|**bigint**|Первичный ключ. Это значение предоставляется в Showplan XML для запросов.|  
|**set_options**|**varbinary(8)**|Битовая маска, отражая состояние некоторых параметров SET. Дополнительные сведения см. в разделе [sys.dm_exec_plan_attributes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md).|  
|**language_id**|**smallint**|Идентификатор языка. Дополнительные сведения см. в разделе [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).|  
|**date_format**|**smallint**|Формат даты. Дополнительные сведения см. в разделе [SET DATEFORMAT (Transact-SQL)](../../t-sql/statements/set-dateformat-transact-sql.md).|  
|**date_first**|**tinyint**|Первое значение даты. Дополнительные сведения см. в разделе [SET DATEFIRST (Transact-SQL)](../../t-sql/statements/set-datefirst-transact-sql.md).|  
|**status**|**varbinary(2)**|Битовую маску, которая указывает тип запроса или контекст, в котором был выполнен запрос. <br />Значение столбца может быть сочетанием сразу несколько флагов (выражено в шестнадцатеричном формате):<br /><br /> 0x0 — обычных запросов (определенные флаги не)<br /><br /> 0x1 — запрос, который был выполнен через один из API-интерфейсы хранимые процедуры курсора<br /><br /> 0x2 — запроса на уведомление<br /><br /> 0x4 — внутренний запрос<br /><br /> 0x8 — auto параметризованного запроса без универсальной параметризации<br /><br /> 0x10 — выборка курсора обновить запрос<br /><br /> 0x20 — запрос, который используется в запросы на обновление курсора<br /><br /> 0x40 – первоначальный результирующий набор возвращается, если курсор открывается (курсор автоматически выборки)<br /><br /> 0x80 – зашифрованных запросов<br /><br /> 0x100 - запроса в контексте предиката безопасности на уровне строк|  
|**required_cursor_options**|**int**|Параметры курсора, указанные пользователем, такие как тип курсора.|  
|**acceptable_cursor_options**|**int**|Параметры курсора, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может неявно преобразовывать для поддержания выполнения инструкции.|  
|**merge_action_type**|**smallint**|Тип плана выполнения триггера, используемого в результате **СЛИЯНИЯ** инструкции.<br /><br /> 0 указывает план без триггеров, план триггеров, который не выполняется в результате **СЛИЯНИЯ** инструкции или план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкцию, которая только определяет **Удалить** действие.<br /><br /> 1 указывает **вставить** план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкции.<br /><br /> 2 указывает **обновление** план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкции.<br /><br /> 3 указывает **удалить** план триггеров, который выполняется в результате **СЛИЯНИЯ** инструкции, содержащей соответствующий **вставить** или **обновления** действие.<br /><br /> <br /><br /> Наличие вложенных триггеров, выполняемых каскадными операциями, это значение, — это **СЛИЯНИЯ** инструкции, запустившей каскад.|  
|**default_schema_id**|**int**|Идентификатор схемы по умолчанию, который используется для разрешения имен, которые не являются полными.|  
|**is_replication_specific**|**bit**|Используется для репликации.|  
|**is_contained**|**varbinary(1)**|1 указывает автономной базы данных.|  
  
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
 [Query Store Stored Procedures (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  (Хранимые процедуры хранилища запросов (Transact-SQL))  
 [sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
