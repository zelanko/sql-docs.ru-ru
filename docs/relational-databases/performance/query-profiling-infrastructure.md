---
title: Инфраструктура профилирования запросов | Документация Майкрософт
ms.custom: ''
ms.date: 11/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual - "query plans [SQL Server]" - "execution plans [SQL Server]" - "query profiling" - "lightweight query profiling" - "lightweight profiling" - "lwp"
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: e0ee0bc2c99d997d6a44d5ca0e9944e0ae4bfeb3
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617254"
---
# <a name="query-profiling-infrastructure"></a>Инфраструктура профилирования запросов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] предоставляет возможность доступа к сведениям среды выполнения о планах выполнения запросов. При возникновении проблемы с производительностью одним из самых важных действий является получение сведений о том, какая рабочая нагрузка выполняется в данный момент и каким образом происходит управление ресурсами. Для осуществления этого важно иметь доступ к [действительному плану выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md).

Несмотря на то, что для доступности действительного плана запроса необходимо дождаться завершения выполнения запроса, [динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md) может анализировать процесс выполнения запроса в режиме реального времени, по мере передачи управления от одного [оператора плана запроса](../../relational-databases/showplan-logical-and-physical-operators-reference.md) другому. Динамический план запроса отображает общий ход выполнения запроса и текущую статистику выполнения на уровне оператора, например число полученных строк, затраченное время, ход выполнения оператора и т. д. Так как эти данные доступны в режиме реального времени и, чтобы их увидеть, не нужно дожидаться завершения запроса, такая статистика чрезвычайно полезна для отладки проблем с производительностью запросов, таких как долгое или "бесконечное" выполнение запросов.

## <a name="the-standard-query-execution-statistics-profiling-infrastructure"></a>Стандартная инфраструктура профилирования статистики выполнения запросов

*Инфраструктуру профилей статистики выполнения запросов*, или стандартное профилирование, необходимо включить для сбора сведений о планах выполнения, а именно числе строк, использовании ЦП и операциях ввода-вывода. Следующие методы сбора сведений о плане выполнения для **целевого сеанса** используют стандартную инфраструктуру профилирования:

- [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md) 
- [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)
- [Динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md)

> [!NOTE]
> Для динамической статистики запросов в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] используется стандартная инфраструктура профилирования.    
> В более поздних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при включении [упрощенной инфраструктуры профилирования](#lwp) вместо стандартного профилирования используется динамическая статистика запросов.

Следующие методы сбора сведений о плане выполнения глобально для **всех сеансов** используют стандартную инфраструктуру профилирования:

-  Расширенное событие ***query_post_execution_showplan***. Сведения о включении расширенных событий см. в статье [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).  
- Событие трассировки **Showplan XML** в [трассировке SQL](../../relational-databases/sql-trace/sql-trace.md) и [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md). Дополнительные сведения об этом событии трассировки см. в статье [Showplan XML, класс событий](../../relational-databases/event-classes/showplan-xml-event-class.md).

При выполнении сеанса расширенного события, использующего событие *query_post_execution_showplan*, также заполняется динамическое административное представление [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md), которое включает динамическую статистику запросов для всех сеансов при помощи [монитора активности](../../relational-databases/performance-monitor/activity-monitor.md) или прямого запроса динамического административного представления. Дополнительные сведения см. в статье [Live Query Statistics](../../relational-databases/performance/live-query-statistics.md).

## <a name="lwp"></a> Упрощенная инфраструктура профилирования статистики выполнения запросов

Начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] была введена новая *упрощенная инфраструктура профилирования статистики выполнения запросов*, или **упрощенное профилирование**. 

> [!NOTE]
> Хранимые процедуры, скомпилированные в собственном коде, не поддерживаются в упрощенном профилировании.  

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v1"></a>Упрощенная инфраструктура профилирования статистики выполнения запросов версии 1

**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 2 (SP2) по [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). 
  
Начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] потребление ресурсов при сборе сведений о планах выполнения было снижено путем введения упрощенного профилирования. В отличие от стандартного, упрощенное профилирование не собирает сведения о ЦП среды выполнения. Однако упрощенное профилирование по-прежнему собирает сведения о количестве строк и сведения об использовании операций ввода-вывода.

Также было добавлено новое расширенное событие ***query_thread_profile***, использующее упрощенное профилирование. Это расширенное событие предоставляет статистику выполнения по операторам, позволяя получить больше сведений о производительности каждого узла и потока. Ниже приведен пример сеанса, использующего это расширенное событие.

```sql
CREATE EVENT SESSION [NodePerfStats] ON SERVER
ADD EVENT sqlserver.query_thread_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

> [!NOTE]
> Дополнительные сведения о снижении потребления ресурсов профилированием запросов см. в записи блога [Developers Choice: Query progress - anytime, anywhere](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) (Выбор разработчика: ход выполнения запроса — всегда и везде). 

При выполнении сеанса расширенного события, использующего событие *query_thread_profile*, также заполняется динамическое административное представление [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) с помощью упрощенного профилирования, которое включает динамическую статистику запросов для всех сеансов при помощи [монитора активности](../../relational-databases/performance-monitor/activity-monitor.md) или прямого запроса динамического административного представления.

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v2"></a>Упрощенная инфраструктура профилирования статистики выполнения запросов версии 2

**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) по [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]). 

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 включает переработанную версию упрощенного профилирования с минимальным потреблением ресурсов. Упрощенное профилирование можно также включить глобально с помощью [флага трассировки 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) в версиях, указанных выше в поле *Применимо к*. Новая функция динамического управления [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) введена для возвращения плана выполнения запроса для активных запросов.

Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 CU3 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU11, если упрощенное профилирование не включено глобально, можно использовать [указание запроса USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint) с новым аргументом **QUERY_PLAN_PROFILE** для включения упрощенного профилирования на уровне запроса для любого сеанса. После завершения запроса, содержащего это новое указание, также выводится новое расширенное событие ***query_plan_profile***, предоставляющее действительный план выполнения в формате XML, аналогично расширенному событию *query_post_execution_showplan*. Ниже приведен пример сеанса, использующего это расширенное событие.

```sql
CREATE EVENT SESSION [PerfStats_LWP_Plan] ON SERVER
ADD EVENT sqlserver.query_plan_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v3"></a>Упрощенная инфраструктура профилирования статистики выполнения запросов версии 3

**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)])

[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] включает в себя заново переработанную версию упрощенного профилирования, собирающего данные о количестве строк для всех выполнений. В [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] упрощенное профилирование включено по умолчанию, и флаг трассировки 7412 не оказывает влияния.

## <a name="remarks"></a>Remarks

> [!IMPORTANT]
> Из-за возможных случайных нарушений прав доступа во время выполнения мониторинга хранимой процедуры, которая ссылается на [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md), необходимо установить исправление [4078596 КБ](http://support.microsoft.com/help/4078596) на [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)].

Начиная с упрощенного профилирования версии 2, благодаря его низкому потреблению ресурсов, любой сервер, у которого нет перегрузки ЦП, может выполнять упрощенное профилирование **непрерывно**. Это позволяет специалистам по работе с базами данных в любое время подключаться к любому запущенному выполнению, например с помощью монитора активности или прямого запроса `sys.dm_exec_query_profiles`, и получать план запроса со статистикой времени выполнения.

Дополнительные сведения о снижении потребления ресурсов профилированием запросов см. в записи блога [Developers Choice: Query progress - anytime, anywhere](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) (Выбор разработчика: ход выполнения запроса — всегда и везде). 

## <a name="see-also"></a>См. также:  
 [Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Средства контроля и настройки производительности](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)     
 [Монитор активности](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [Мониторинг активности системы с помощью расширенных событий](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)      
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Справочник по логическим и физическим операторам Showplan](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
 [Действительный план выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md)    
 [Динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md)      
 [Выбор разработчика: сведения о ходе выполнения запросов в любое время и в любом месте](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/)
