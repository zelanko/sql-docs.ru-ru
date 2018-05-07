---
title: sys.database_query_store_options (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 10/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a9ce2b5f63405a0754782e0dddae5584c1b47ee2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает параметры хранилища запросов для этой базы данных.  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Указывает нужный режим работы хранилища запросов, явно устанавливается пользователем.<br /> 0 = выключен. <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(64)**|Текстовое описание нужный режим работы хранилища запросов:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Указывает режим работы хранилища запросов. Помимо списка необходимых состояний, необходимых пользователю фактическое состояние может быть состояние ошибки.<br /> 0 = выключен. <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = ОШИБКА|  
|**actual_state_desc**|**nvarchar(64)**|Текстовое описание фактический режим работы хранилища запросов.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />ERROR<br /><br /> Существуют ситуации, когда фактическое состояние отличается от желаемого состояния.<br /><br /> Хранилище запросов может работать в режиме только для чтения, даже если чтения и записи был определен пользователем. Например, может произойти, если база данных находится в режиме только для чтения или если размер хранилища запросов превышает квоту.<br /><br /> Крайне редко хранилище запросов может оказаться в состоянии ошибки из-за внутренней ошибки. В этом случае хранилище запросов может восстановить, выполнив **sp_query_store_consistency_check** хранимой процедуры в соответствующей базе данных.|  
|**readonly_reason**|**int**|Когда **desired_state_desc** находится в состоянии READ_WRITE и **actual_state_desc** находится в режиме READ_ONLY, **readonly_reason** возвращает немного сопоставления указывает, почему в хранилище запросов режим только для чтения.<br /><br /> 1 — база данных находится в режиме только для чтения<br /><br /> 2 — база данных находится в однопользовательском режиме<br /><br /> 4 — база данных находится в аварийном режиме<br /><br /> 8 — база данных является вторичной репликой (применяется к Always On и Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] георепликации). Это значение можно было эффективно контролировать только через **для чтения** вторичных реплик<br /><br /> 65536 — хранилище запросов достигло предельного размера, задайте для параметра MAX_STORAGE_SIZE_MB.<br /><br /> 131072 — число различных операторов в хранилище запросов достигнут предел внутренней памяти. Рекомендуется удалить запросы, которые не требуется или обновление до более высокого уровня службы для включения передачи хранилище запросов в режиме чтения и записи.<br />Относится только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> 262144 — размер элементов в памяти, ожидающих сохраняются на диске достигнут предел внутренней памяти. Хранилище запросов будет находиться в режиме только для чтения временно до элементов в памяти, сохраняются на диске. <br />Относится только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br />524288 — база данных достигла предельного размера диска. Хранилище запросов является частью пользовательской базы данных, если больше нет свободного места для базы данных, которое означает, что хранилище запросов не может увеличиваться больше.<br />Относится только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. <br /> <br /> Переключение хранилища запросов операций назад режим для чтения и записи см. в разделе **хранилище запросов проверьте непрерывность сбора данных запросов —** раздел [рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md).|  
|**current_storage_size_mb**|**bigint**|Размер хранилища запросов на диске в мегабайтах.|  
|**flush_interval_seconds**|**bigint**|Определяет период для очистки данных в хранилище запросов регулярного на диск. Значение по умолчанию — 900 (15 минут).<br /><br /> Изменение с помощью `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` инструкции.|  
|**interval_length_minutes**|**bigint**|Интервал агрегации статистики. Произвольные значения не допускаются. Используйте один из следующих действий: 1, 5, 10, 15, 30, 60 и 1440 минут. Значение по умолчанию — 60 минут.|  
|**max_storage_size_mb**|**bigint**|Максимальный размер диска для хранилища запросов. Значение по умолчанию — 100 МБ.<br />Для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition значение по умолчанию — 1 ГБ, а для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition — 10 МБ.<br /><br /> Изменение с помощью `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` инструкции.|  
|**stale_query_threshold_days**|**bigint**|Число дней, запросы при отсутствии параметров политики хранятся в хранилище запросов. Значение по умолчанию — 30. Значение 0, чтобы отключить политику хранения.<br />Для выпуска [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition значение по умолчанию — семь дней.<br /><br /> Изменение с помощью `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` инструкции.|  
|**max_plans_per_query**|**bigint**|Ограничивает максимальное количество хранимых планов. Значение по умолчанию — 200. Если достигнуто максимальное значение, хранилище запросов прекращает запись новых планов для этого запроса. Параметр 0 Удаляет ограничение отношении количество записанных планов.<br /><br /> Изменение с помощью `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` инструкции.|  
|**query_capture_mode**|**smallint**|Режим записи активного запроса:<br /><br /> 1 = ALL — записываются все запросы. Это значение по умолчанию конфигурация для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 2 = AUTO - захвата соответствующие запросы на основании выполнения count и потребления ресурсов. Это значение по умолчанию конфигурация для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = NONE — останавливает запись новых запросов. Хранилище запросов будет продолжать сбор статистики компиляции и времени выполнения для запросов, которые уже были записаны. Эта конфигурация используйте осторожно, поскольку можно пропустить для записи важных запросов.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Текстовое описание режим фактические записи хранилища запросов:<br /><br /> ВСЕ (по умолчанию для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> AUTO (по умолчанию для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> None|  
|**size_based_cleanup_mode**|**smallint**|Определяет, будет ли автоматически активирована очистка, когда общий объем данных приблизится к верхней границе ограничения.<br /><br /> 1 = OFF — не будет автоматически активирована Очистка на основе размера.<br /><br /> 2 = AUTO - очистки на основе активируется автоматически при размер на диске достигает 90% от размера **max_storage_size_mb**. Это значение конфигурации по умолчанию.<br /><br />Эта очистка сначала удаляет самые дешевые и самые старые запросы. Он останавливается на 80% max_storage_size_mb.|  
|**size_based_cleanup_mode_desc**|**smallint**|Текстовое описание режима фактическое очистки на основе размер хранилища запросов:<br /><br /> OFF <br /><br /> AUTO (по умолчанию)|  
|**wait_stats_capture_mode**|**smallint**|Элементы управления, является ли хранилище запросов выполняет сбор статистики ожидания. <br /><br /> 0 = выключен. <br /><br /> 1 = включен;<br /> **Область применения**: начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|**wait_stats_mode_capture_desc**|**nvarchar(60)**|Текстовое описание режим записи фактического ожидания статистики: <br /><br /> OFF <br /><br /> (По умолчанию)<br /> **Область применения**: начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW DATABASE STATE** разрешение.  
  
## <a name="see-also"></a>См. также  
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Хранимые процедуры в хранилище запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
