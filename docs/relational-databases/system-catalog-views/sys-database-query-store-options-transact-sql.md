---
title: sys.database_query_store_options (Transact-SQL) | Документация Майкрософт
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9a674efd6c2e7d9db42a0d731e9722fb267830e9
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39552174"
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает параметры Store запроса для этой базы данных.  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Указывает нужный режим работы запроса Store, явно заданных пользователем.<br /> 0 = выключен. <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**Nvarchar(64)**|Текстовое описание нужный режим работы Query Store:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Указывает режим работы запроса Store. Помимо списка необходимых состояний, необходимых пользователю фактическое состояние может быть состояние ошибки.<br /> 0 = выключен. <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = ОШИБКА|  
|**actual_state_desc**|**Nvarchar(64)**|Текстовое описание фактический режим работы запроса Store.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />Ошибка<br /><br /> Существуют ситуации, когда фактическое состояние отличается от желаемого состояния:<br /><br /> Query Store может работать в режиме только для чтения, даже если чтения и записи было указано пользователем. Например, который может произойти, если база данных находится в режиме только для чтения или запроса Store размер превышает квоту.<br /><br /> Крайне редко Query Store могут быть сохранены в состоянии ошибки из-за внутренней ошибки. В этом случае запрос Store удалось восстановить, выполнив **sp_query_store_consistency_check** хранимую процедуру в этой базы данных.|  
|**readonly_reason**|**int**|Когда **desired_state_desc** находится в режиме READ_WRITE и **actual_state_desc** находится в режиме READ_ONLY, **readonly_reason** возвращает немного карты необходимо указать причину Store запроса находится в режим только для чтения.<br /><br /> 1 — база данных находится в режиме только для чтения<br /><br /> 2 — база данных находится в однопользовательском режиме<br /><br /> 4 — база данных находится в аварийном режиме<br /><br /> 8 — база данных является вторичной репликой (применяется к Always On и Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] георепликации). Это значение можно было эффективно контролировать только через **для чтения** вторичных реплик<br /><br /> 65536 Store запрос был достигнут предельный размер, установленное параметром MAX_STORAGE_SIZE_MB.<br /><br /> 131072 — число различных инструкций в Store запросов достигнут предел внутренней памяти. Рекомендуется удалить запросы, которые не требуется или обновлении до более высокого уровня службы, передачу Store запросов в режим чтения и записи.<br />Относится только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> 262144 — размер элементов в памяти, ожидающих сохраняются на диске был достигнут предел внутренней памяти. Query Store будет находиться в режиме только для чтения, временно, пока не элементы в памяти сохраняются на диске. <br />Относится только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br />524288 — базы данных был достигнут предельный размер диска. Query Store является частью пользовательской базы данных, поэтому если больше нет свободного места для базы данных, которое означает, что Store запроса не может продолжать увеличиваться больше.<br />Относится только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. <br /> <br /> Для переключения операции Query Store обратно режим чтения и записи, см. в разделе **непрерывность сбора данных запросов является проверка запроса Store** раздел [оптимальным образом с помощью Query Store](../../relational-databases/performance/best-practice-with-the-query-store.md).|  
|**current_storage_size_mb**|**bigint**|Размер запроса Store на диске в мегабайтах.|  
|**flush_interval_seconds**|**bigint**|Определяет период для регулярного записью Store запроса данных на диск. Значение по умолчанию — 900 (15 минут).<br /><br /> Изменение с помощью `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` инструкции.|  
|**interval_length_minutes**|**bigint**|Статистика интервала статистической обработки. Произвольные значения не допускаются. Используйте один из следующих: 1, 5, 10, 15, 30, 60 и 1440 минут. Значение по умолчанию — 60 минут.|  
|**max_storage_size_mb**|**bigint**|Максимальный размер диска для запроса Store. Значение по умолчанию — 100 МБ.<br />Для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition значение по умолчанию — 1 ГБ, а для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition — 10 МБ.<br /><br /> Изменение с помощью `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` инструкции.|  
|**stale_query_threshold_days**|**bigint**|Количество дней, запросы при отсутствии параметров политики, хранятся в Store запроса. Значение по умолчанию — 30. Чтобы отключить политику хранения необходимо присвоить значение 0.<br />Для выпуска [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition значение по умолчанию — семь дней.<br /><br /> Изменение с помощью `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` инструкции.|  
|**max_plans_per_query**|**bigint**|Ограничивает максимальное количество хранимых планов. Значение по умолчанию — 200. После достижения максимального значения Store запросов прекращает запись новых планов для этого запроса. Параметр 0 Удаляет ограничение в зависимости от того, количество записанных планов.<br /><br /> Изменение с помощью `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` инструкции.|  
|**query_capture_mode**|**smallint**|Режим записи текущего активного запроса:<br /><br /> 1 = ALL — записываются все запросы. Это значение конфигурации по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 2 = AUTO — записываются соответствующие запросы на основе потребления count и ресурсов выполнения. Это значение конфигурации по умолчанию для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = NONE — прекратит запись новых запросов. Хранилище запросов будет продолжать сбор статистики компиляции и времени выполнения для запросов, которые уже были записаны. Используйте эту конфигурацию осторожно, поскольку можно пропустить запись важных запросов.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Текстовое описание фактическую запись режим Query Store:<br /><br /> ВСЕ (по умолчанию для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> АВТОМАТИЧЕСКИ (по умолчанию для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> None|  
|**size_based_cleanup_mode**|**smallint**|Определяет, будет ли автоматически активирована очистка, когда общий объем данных приблизится к верхней границе ограничения.<br /><br /> 1 = OFF — не будет автоматически активирована Очистка на основе размера.<br /><br /> 2 = AUTO - Очистка на основе будет ли автоматически активирована, когда размер на диске достигает 90% от размера **max_storage_size_mb**. Это значение конфигурации по умолчанию.<br /><br />Эта очистка сначала удаляет самые дешевые и самые старые запросы. Она останавливается приблизительно 80% max_storage_size_mb.|  
|**size_based_cleanup_mode_desc**|**smallint**|Текстовое описание фактическую очистку на основе размера режим Query Store:<br /><br /> OFF <br /><br /> АВТОМАТИЧЕСКИ (по умолчанию)|  
|**wait_stats_capture_mode**|**smallint**|Элементы управления, выполняет ли запрос Store снимок статистики ожидания. <br /><br /> 0 = выключен. <br /><br /> 1 = включен;<br /> **Применимо к**: с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|**wait_stats_mode_capture_desc**|**nvarchar(60)**|Текстовое описание режим записи статистики фактического ожидания: <br /><br /> OFF <br /><br /> (По умолчанию)<br /> **Применимо к**: с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
  
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
 [Query Store хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
