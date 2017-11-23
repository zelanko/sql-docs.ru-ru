---
title: "sys.query_store_plan (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_PLAN_TSQL
- SYS.QUERY_STORE_PLAN
- SYS.QUERY_STORE_PLAN_TSQL
- QUERY_STORE_PLAN
dev_langs: TSQL
helpviewer_keywords:
- query_store_plan catalog view
- sys.query_store_plan catalog view
ms.assetid: b4d05439-6360-45db-b1cd-794f4a64935e
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0950cf33d112d299de615a702d0fbac7cbfdc0e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysquerystoreplan-transact-sql"></a>sys.query_store_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Содержит сведения о каждом плане выполнения, связанные с запросом.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**bigint**|Первичный ключ.|  
|**query_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_query &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md).|  
|**plan_group_id**|**bigint**|Идентификатор группы плана. Запросы с курсорами обычно требуется несколько (заполнения и выборки) планов. Заполнение fetch планов и компилируются вместе в одной группе.<br /><br /> 0 означает, что план не входит в группу.|  
|**engine_version**|**nvarchar(32)**|Версия подсистемы, использованными при компиляции плана в **«Главная.вспомогательная.сборка.редакция»** формат.|  
|**compatibility_level**|**smallint**|Уровень совместимости базы данных из базы данных, указанных в запросе.|  
|**фиксировать**|**binary(8)**|MD5-хэш отдельных плана.|  
|**query_plan**|**nvarchar(max)**|Showplan XML для плана запроса.|  
|**is_online_index_plan**|**bit**|План был использован во время построения индекса в сети.|  
|**is_trivial_plan**|**bit**|План — обычный план (выходные данные на этапе 0 оптимизатор запросов).|  
|**is_parallel_plan**|**bit**|План работает параллельно.|  
|**is_forced_plan**|**bit**|План будет помечен как принудительно, когда пользователь выполняет хранимую процедуру **sys.sp_query_store_force_plan**. Механизм принудительного *не гарантирует* что именно этот план будет использоваться для запроса, который ссылается **query_id**. Форсирование планов вызывает запрос компилируется еще раз и обычно создает точно такие же или аналогичные плана для плана, на который указывает **plan_id**. Если принудительное выполнение плана завершится неудачно, **force_failure_count** увеличивается и **last_force_failure_reason** заполняется причина сбоя.|  
|**is_natively_compiled**|**bit**|План содержит процедуры, скомпилированные в собственном коде оптимизированные для памяти. (0 = FALSE, 1 = TRUE).|  
|**force_failure_count**|**bigint**|Количество попыток принудительного плана произошел сбой. Может быть увеличен только в том случае, когда запрос перекомпилируется (*не при каждом выполнении*). Он обнуляется каждый раз **is_plan_forced** меняется с **FALSE** для **TRUE**.|  
|**last_force_failure_reason**|**int**|Причина, почему форсирование плана не удалось.<br /><br /> 0: не ошибка, в противном случае номер ошибки, вызвавшей сбой принудительного<br /><br /> 8637: ONLINE_INDEX_BUILD<br /><br /> 8683: INVALID_STARJOIN<br /><br /> 8684: ВРЕМЯ_ОЖИДАНИЯ<br /><br /> 8689: NO_DB<br /><br /> 8690: HINT_CONFLICT<br /><br /> 8691: SETOPT_CONFLICT<br /><br /> 8694: DQ_NO_FORCING_SUPPORTED<br /><br /> 8698: NO_PLAN<br /><br /> 8712: NO_INDEX<br /><br /> 8713: VIEW_COMPILE_FAILED<br /><br /> \<другое значение >: GENERAL_FAILURE|  
|**last_force_failure_reason_desc**|**nvarchar(128)**|Текстовое описание last_force_failure_reason_desc.<br /><br /> ONLINE_INDEX_BUILD: запрос пытается изменить данные, а целевая таблица имеет индекс, который строится в интерактивном режиме<br /><br /> INVALID_STARJOIN: план содержит недопустимую спецификацию StarJoin<br /><br /> Время_ожидания: Оптимизатор превысил количество разрешенных операций во время поиска плана, заданные в форсированном плане<br /><br /> NO_DB: Базы данных, указанной в плане не существует<br /><br /> HINT_CONFLICT: Запрос невозможно скомпилировать, поскольку план конфликтует с подсказки в запросе<br /><br /> DQ_NO_FORCING_SUPPORTED: Не удается выполнить запрос, поскольку план конфликтует с использованием распределенного запроса или полнотекстовых операций.<br /><br /> NO_PLAN: Обработчику запросов не удалось предоставить план запроса, так как не удалось проверить принудительный план для запроса<br /><br /> Внимание: Индекс, заданный в плане, больше не существует<br /><br /> VIEW_COMPILE_FAILED: Не удалось принудительно план запроса из-за проблемы в индексированное представление, указанное в плане<br /><br /> GENERAL_FAILURE: принудительное ошибка (не связанная с причинами выше)|  
|**count_compiles**|**bigint**|Планирование Статистика компиляции.|  
|**initial_compile_start_time**|**datetimeoffset**|Планирование Статистика компиляции.|  
|**last_compile_start_time**|**datetimeoffset**|Планирование Статистика компиляции.|  
|**last_execution_time**|**datetimeoffset**|Время последнего выполнения последней ссылается время окончания или плана запроса.|  
|**avg_compile_duration**|**float**|Планирование Статистика компиляции.|  
|**last_compile_duration**|**bigint**|Планирование Статистика компиляции.|  
  
## <a name="plan-forcing-limitations"></a>Ограничения форсирования планов
Хранилище запросов имеет механизм, позволяющий оптимизатору запросов принудительно применить определенный план выполнения. Но существуют некоторые ограничения, которые могут препятствовать применению плана. 

Во-первых, когда план содержит следующие конструкции:
* Инструкция INSERT BULK.
* Инструкция INSERT BULK.
* ссылка на внешнюю таблицу;
* распределенный запрос или полнотекстовые операции;
* использование глобальных запросов. 
* Курсоры
* Недопустимая спецификация соединения типа "звезда" 

Во-вторых, когда объекты, от которых зависит план, больше не доступны:
* база данных (если база данных, где план был создан изначально, больше не существует);
* индекс (больше не существует или отключен).

Наконец, проблемы с самим планом:
* недопустим для запроса;
* оптимизатор запросов превысил количество разрешенных операций;
* неправильно сформированный XML-код плана.

## <a name="permissions"></a>Permissions  
 Требуется **VIEW DATABASE STATE** разрешение.  
  
## <a name="see-also"></a>См. также:  
 [sys.database_query_store_options &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_query &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Хранимые процедуры &#40; в хранилище запросов Transact-SQL &#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
