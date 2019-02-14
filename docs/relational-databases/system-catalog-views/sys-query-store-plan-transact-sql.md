---
title: sys.query_store_plan (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_PLAN_TSQL
- SYS.QUERY_STORE_PLAN
- SYS.QUERY_STORE_PLAN_TSQL
- QUERY_STORE_PLAN
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_plan catalog view
- sys.query_store_plan catalog view
ms.assetid: b4d05439-6360-45db-b1cd-794f4a64935e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fc6eca7f1b28434c42579181c04d0fe9cb2f2922
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56231111"
---
# <a name="sysquerystoreplan-transact-sql"></a>sys.query_store_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Содержит сведения о каждом плане выполнения, связанного с запросом.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|
|**plan_id**|**bigint**|Первичный ключ.|  
|**query_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md).|  
|**plan_group_id**|**bigint**|Идентификатор группы плана. Запросы с курсорами обычно требуется несколько (заполнения и выборки) планы. Заполнения и выборки планы, которые компилируются вместе находятся в той же группе.<br /><br /> 0 означает, что план не находится в группе.|  
|**engine_version**|**nvarchar(32)**|Версия ядра, используемые для компиляции плана в **«основная.дополнительная.сборка.редакция»** формат.|  
|**compatibility_level**|**smallint**|Уровень совместимости базы данных базы данных, указанных в запросе.|  
|**query_plan_hash**|**binary(8)**|MD5-хэш отдельных плана.|  
|**query_plan**|**nvarchar(max)**|Showplan XML для плана запроса.|  
|**is_online_index_plan**|**bit**|План был использован во время построения индекса в сети. <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**is_trivial_plan**|**bit**|План — это упрощенный план (выходные данные на этапе 0 оптимизатор запросов). <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**is_parallel_plan**|**bit**|План — параллельное выполнение. <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать один (1).|  
|**is_forced_plan**|**bit**|План будет помечена как принудительно, когда пользователь выполняет хранимую процедуру **sys.sp_query_store_force_plan**. Механизм принудительного *не гарантирует* что именно этот план будет использоваться для запроса, который ссылается **query_id**. Форсирование планов вызывает запрос, чтобы скомпилировать еще раз и обычно создает точно одинаковые или похожие плана для плана, который ссылается **plan_id**. Если форсирование планов не работает, **force_failure_count** увеличивается и **last_force_failure_reason** заполняется причину сбоя. <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**is_natively_compiled**|**bit**|План содержит процедуры, скомпилированные в собственном коде оптимизированные для памяти. (0 = FALSE, 1 = TRUE). <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**force_failure_count**|**bigint**|Количество попыток принудительного плана произошел сбой. Он может быть увеличен только в том случае, когда запрос перекомпилируется (*не при каждом выполнении*). Он сбрасывается на 0 каждый раз **is_plan_forced** меняется с **FALSE** для **TRUE**. <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**last_force_failure_reason**|**int**|Причина, почему сбой форсирования плана.<br /><br /> 0: не ошибка, в противном случае номер ошибки, вызвавшей Принудительная переход на другой<br /><br /> 8637: ONLINE_INDEX_BUILD<br /><br /> 8683: INVALID_STARJOIN<br /><br /> 8684: TIME_OUT<br /><br /> 8689: NO_DB<br /><br /> 8690: HINT_CONFLICT<br /><br /> 8691: SETOPT_CONFLICT<br /><br /> 8694: DQ_NO_FORCING_SUPPORTED<br /><br /> 8698: NO_PLAN<br /><br /> 8712: ВНИМАНИЕ<br /><br /> 8713: VIEW_COMPILE_FAILED<br /><br /> \<другое значение >: GENERAL_FAILURE <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**last_force_failure_reason_desc**|**nvarchar(128)**|Текстовое описание last_force_failure_reason_desc.<br /><br /> ONLINE_INDEX_BUILD: запрос пытается изменить данные, хотя целевая таблица имеет индекс, который строится через Интернет<br /><br /> INVALID_STARJOIN: план содержит недопустимую спецификацию StarJoin<br /><br /> ВРЕМЯ_ОЖИДАНИЯ: Оптимизатор превысил количество разрешенных операций во время поиска плана, заданные принудительного плана<br /><br /> NO_DB: Не существует в базе данных, указанной в плане<br /><br /> HINT_CONFLICT: Запрос невозможно скомпилировать, так как план конфликтует с указанием запроса<br /><br /> DQ_NO_FORCING_SUPPORTED: Невозможно выполнить запрос, поскольку план конфликтует с использованием распределенного запроса или операций полнотекстового поиска.<br /><br /> NO_PLAN: Обработчику запросов не удалось создать план запроса, поскольку не удалось проверить принудительный план был допустимым для запроса<br /><br /> ВНИМАНИЕ: Индекс, заданный в план больше не существует<br /><br /> VIEW_COMPILE_FAILED: Не удалось принудительно использовать план запроса из-за проблемы в индексированное представление, указанное в плане<br /><br /> GENERAL_FAILURE: принудительное ошибка (не реализуются посредством выше причинам) <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *NONE*.|  
|**count_compiles**|**bigint**|Планирование статистики компиляции.|  
|**initial_compile_start_time**|**datetimeoffset**|Планирование статистики компиляции.|  
|**last_compile_start_time**|**datetimeoffset**|Планирование статистики компиляции.|  
|**last_execution_time**|**datetimeoffset**|Время последнего выполнения относится к последней время окончания/плана запроса.|  
|**avg_compile_duration**|**float**|Планирование статистики компиляции. <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**last_compile_duration**|**bigint**|Планирование статистики компиляции. <br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**plan_forcing_type**|**int**|Тип принудительного применения плана.<br /><br />0: None<br /><br />1: MANUAL<br /><br />2. AUTO|  
|**plan_forcing_type_desc**|**nvarchar(60)**|Text description of plan_forcing_type.<br /><br />НЕТ: Форсирование планов не<br /><br />ВРУЧНУЮ: План, принудительно задается пользователем<br /><br />АВТО: Принудительно используемый план автоматической настройкой|  

## <a name="plan-forcing-limitations"></a>Ограничения принудительного использования планов
Хранилище запросов имеет механизм, позволяющий оптимизатору запросов принудительно применить определенный план выполнения. Но существуют некоторые ограничения, которые могут препятствовать применению плана. 

Во-первых, когда план содержит следующие конструкции:
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

## <a name="permissions"></a>Разрешения  
 Требуется **VIEW DATABASE STATE** разрешение.  
  
## <a name="see-also"></a>См. также  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Query Store хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
