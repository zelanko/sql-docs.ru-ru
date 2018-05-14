---
title: Использование объектов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server performance [SQL Server], objects for monitoring
- database monitoring [SQL Server], objects for monitoring
- charts [SQL Server]
- System Monitor [SQL Server], counters
- counters [SQL Server], listed
- objects [SQL Server], performance monitoring
- objects [SQL Server], Windows System Monitor
- performance counters [SQL Server], about performance counters
- System Monitor [SQL Server], objects
- performance counters [SQL Server]
- counters [SQL Server], about performance counters
- tuning databases [SQL Server], objects for monitoring
- database performance [SQL Server], objects for monitoring
- SQL Server, objects
- monitoring performance [SQL Server], objects for monitoring
- Windows System Monitor [SQL Server], objects
- Windows System Monitor [SQL Server], counters
- counters [SQL Server]
- performance counters [SQL Server], listed
ms.assetid: bcd731b1-3c4e-4086-b58a-af7a3af904ad
caps.latest.revision: 56
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bbc182e6fc9298a262fe4efb9560fb5c0cc67109
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="use-sql-server-objects"></a>Использование объектов SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут использоваться системным монитором для мониторинга активности на компьютере, где запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Объект представляет собой любой ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например блокировку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или процесс Windows. В каждом объекте содержатся один или более счетчиков, определяющих различные аспекты объектов для мониторинга. Например, объект **Блокировки SQL Server** содержит счетчики с названием **Количество взаимоблокировок/с** и **Превышений времени ожидания блокировки в секунду**.  
  
 В некоторых объектах содержится несколько экземпляров разных ресурсов данного типа, существующих на компьютере. Например, у типа объектов **Процессор** будет несколько экземпляров, если в системе установлено несколько процессоров. У типа объектов **Базы данных** будет по одному экземпляру для каждой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. У некоторых типов объектов (например, у объекта **Диспетчер памяти** ) может быть только один экземпляр. Если у типа объектов несколько экземпляров, можно добавлять счетчики для отслеживания статистики каждого экземпляра или, во многих случаях, для всех экземпляров сразу. Счетчики для экземпляра по умолчанию отображаются в формате **SQLServer:***\<имя_объекта>*. Счетчики для именованных экземпляров отображаются в формате **MSSQL$***\<имя_экземпляра>***:***\<имя_счетчика>* или **SQLAgent$***\<имя_экземпляра>***:***\<имя_счетчика>*.  
  
 Добавляя или удаляя счетчики в диаграмму и сохраняя ее параметры, можно указать объекты и счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которых будут считываться данные при запуске системного монитора.  
  
 Можно настроить системный монитор для отображения статистики любого счетчика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, можно задать пороговое значение для любого счетчика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и затем формировать предупреждение о превышении порога. Дополнительные сведения о настройке предупреждения см. в разделе [Создание предупреждения для базы данных SQL Server](../../relational-databases/performance-monitor/create-a-sql-server-database-alert.md).  
  
> [!TIP]  
>  Можно также вернуть значения счетчика производительности, отправив запрос динамическому представлению управления [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статистика отображается, только если установлен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При остановке и повторном запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отображение статистик прерывается и возобновляется автоматически. Также обратите внимание, что счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] видны в оснастке системного монитора, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущен. На кластеризованном экземпляре счетчики производительности функционируют только на том узле, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Объекты производительности агента SQL Server](#SQLServerAgentPOs)  
  
-   [Объекты производительности компонента Service Broker](#ServiceBrokerPOs)  
  
-   [Объекты производительности SQL Server](#SQLServerPOs)  
  
-   [Объекты производительности репликации SQL Server](#SQLServerReplicationPOs)  
  
-   [Счетчики каналов службы SSIS](#SsisPipelineCounters)  
  
-   [Необходимые разрешения](#RequiredPermissions)  
  
##  <a name="SQLServerAgentPOs"></a> Объекты производительности агента SQL Server  
 Следующая таблица содержит список объектов измерения производительности для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|[SQLAgent:Alerts](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Предоставляет сведения о предупреждениях агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Предоставляет сведения о заданиях агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Предоставляет сведения о шагах заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:Statistics](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Предоставляет общие сведения об агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
##  <a name="ServiceBrokerPOs"></a> Объекты производительности компонента Service Broker  
 Следующая таблица содержит список объектов измерения производительности для компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|[SQLServer:Broker Activation](../../relational-databases/performance-monitor/sql-server-broker-activation-object.md)|Предоставляет сведения об активированных задачах компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|[SQLServer:Broker Statistics](../../relational-databases/performance-monitor/sql-server-broker-statistics-object.md)|Предоставляет общие сведения о компоненте [!INCLUDE[ssSB](../../includes/sssb-md.md)] .|  
|[SQLServer: транспорт посредника](../../relational-databases/performance-monitor/sql-server-broker-dbm-transport-object.md)|Предоставляет сведения о сетевой работе компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .|  
  
##  <a name="SQLServerPOs"></a> Объекты производительности SQL Server  
 В следующей таблице описаны объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|[SQLServer:Access Methods](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)|Ищет и измеряет выделения ресурсов для объектов баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, число поисков в индексе или число страниц, выделенных для индексов и данных).|  
|[SQLServer:Backup Device](../../relational-databases/performance-monitor/sql-server-backup-device-object.md)|Предоставляет сведения об устройствах резервного копирования, использующихся в операциях резервного копирования и восстановления, например пропускную способность устройства.|  
|[SQLServer:Batch Resp Statistics](../../relational-databases/performance-monitor/sql-server-batch-resp-statistics-object.md)|Счетчики для отслеживания времени пакетного отклика SQL.| 
|[SQLServer: Buffer Manager](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)|Предоставляет сведения о буферах памяти, использующихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например **свободная память** и **коэффициент попадания в кэш буфера**.|  
|[SQL Server:Buffer Node](../../relational-databases/performance-monitor/sql-server-buffer-node.md)|Предоставляет сведения о том, как часто [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрашивает и получает доступ к свободным страницам.|  
|[SQLServer:Catalog Metadata](../../relational-databases/performance-monitor/sql-server-catalog-metadata-object.md)|Определяет объект диспетчера метаданных каталога для SQL Server.| 
|[SQLServer: среда CLR](../../relational-databases/performance-monitor/sql-server-clr-object.md)|Предоставляет сведения о языке среды выполнения CLR.|  
|[SQLServer:Columnstore](../../relational-databases/performance-monitor/sql-server-columnstore-object.md)|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> Предоставляет информацию о группах строк и сегментах для индексов columnstore.|  
|[SQLServer:Cursor Manager by Type](../../relational-databases/performance-monitor/sql-server-cursor-manager-by-type-object.md)|Предоставляет сведения о курсорах.|  
|[SQLServer:Cursor Manager Total](../../relational-databases/performance-monitor/sql-server-cursor-manager-total-object.md)|Предоставляет сведения о курсорах.|  
|[SQLServer:Database Mirroring](../../relational-databases/performance-monitor/sql-server-database-mirroring-object.md)|Предоставляет сведения о зеркальном отображении баз данных.|  
|[SQLServer: базы данных](../../relational-databases/performance-monitor/sql-server-databases-object.md)|Предоставляет сведения о базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например объем доступного свободного места для журналов или количество активных транзакций в базе данных. Может существовать несколько экземпляров этого объекта.|  
|[SQL Server: устаревшие функции](../../relational-databases/performance-monitor/sql-server-deprecated-features-object.md)|Подсчитывает частоту использования устаревших функций.|  
|[SQLServer: статистика выполнений](../../relational-databases/performance-monitor/sql-server-execstatistics-object.md)|Предоставляет сведения о статистике выполнения.|  
|[SQL Server:External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> Предоставляет сведения о выполнении внешних скриптов.|  
|[SQLServer:FileTable](../../relational-databases/performance-monitor/sql-server-filetable-object.md)|Статистика, связанная с FileTable и доступом без использования транзакций.|  
|[SQLServer: General Statistics](../../relational-databases/performance-monitor/sql-server-general-statistics-object.md)|Предоставляет сведения об активности сервера в общем, например количество пользователей, подключенных к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQL Server: реплика доступности HADR](../../relational-databases/performance-monitor/sql-server-availability-replica.md)|Предоставляет сведения о репликах доступности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .|  
|[SQL Server: реплика базы данных HADR](../../relational-databases/performance-monitor/sql-server-database-replica.md)|Содержит сведения о репликах базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .|  
|[SQLServer:Latches](../../relational-databases/performance-monitor/sql-server-latches-object.md)|Предоставляет сведения о кратковременных блокировках внутренних ресурсов, например страниц баз данных, использующихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQLServer:Locks](../../relational-databases/performance-monitor/sql-server-locks-object.md)|Предоставляет сведения об отдельных запросах на блокировку, сделанных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например время ожидания блокировки и взаимоблокировки. Может существовать несколько экземпляров этого объекта.|  
|[SQLServer:LogPool FreePool](../../relational-databases/performance-monitor/sql-server-logpool-freepool-object.md)|Описывает статистику свободного пула внутри пула журналов.|
|[SQLServer:Memory Broker Clerks](../../relational-databases/performance-monitor/sql-server-memory-broker-clerks-object.md)|Статистика, связанная с клерками брокера памяти.|
|[SQLServer:Memory Manager](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)|Предоставляет сведения об использовании памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например общее число выделенных на данный момент структур блокировок.|  
|[SQLServer:Plan Cache](../../relational-databases/performance-monitor/sql-server-plan-cache-object.md)|Предоставляет сведения о кэше [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующемся для хранения таких объектов, как хранимые процедуры, триггеры и планы запросов.|  
|[SQLServer:Query Store](../../relational-databases/performance-monitor/sql-server-query-store-object.md)|Предоставляет сведения о хранилище запросов.|  
|[SQLServer:Resource Pool Stats](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)|Предоставляет статистические данные о пуле ресурсов регулятора ресурсов.|  
|[SQLServer:SQL Errors](../../relational-databases/performance-monitor/sql-server-sql-errors-object.md)|Предоставляет сведения об ошибках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLServer:SQL Statistics](../../relational-databases/performance-monitor/sql-server-sql-statistics-object.md)|Предоставляет сведения о разных аспектах запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] , например число пакетов инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , полученных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQLServer:Transactions](../../relational-databases/performance-monitor/sql-server-transactions-object.md)|Предоставляет сведения об активных транзакциях в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например общее число транзакций и число транзакций моментальных снимков.|  
|[SQLServer:User Settable](../../relational-databases/performance-monitor/sql-server-user-settable-object.md)|Выполняет пользовательское наблюдение. Каждый счетчик может быть пользовательской хранимой процедурой или любой инструкцией [!INCLUDE[tsql](../../includes/tsql-md.md)] , возвращающей значение, которое можно отслеживать.|  
|[SQLServer:Wait Statistics](../../relational-databases/performance-monitor/sql-server-wait-statistics-object.md)|Предоставляет сведения об ожиданиях.|  
|[SQLServer:Workload Group Stats](../../relational-databases/performance-monitor/sql-server-workload-group-stats-object.md)|Предоставляет статистические данные о группе рабочей нагрузки регулятора ресурсов.|  
  
##  <a name="SQLServerReplicationPOs"></a> Объекты производительности репликации SQL Server  
 Следующая таблица содержит список объектов измерения производительности репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|**SQLServer: агенты репликации**<br /><br /> **SQLServer: моментальный снимок репликации**<br /><br /> **SQLServer: чтение журнала репликаций**<br /><br /> **SQLServer: распространитель репликации**<br /><br /> **SQLServer: репликация слиянием**<br /><br /> Дополнительные сведения см. в статье [Monitoring Replication with System Monitor](../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).|Содержит сведения о действиях агента репликации.|  
  
##  <a name="SsisPipelineCounters"></a> Счетчики каналов службы SSIS  
 Сведения о счетчике **Конвейер служб SSIS** см. в разделе [Счетчики производительности](../../integration-services/performance/performance-counters.md).  
  
##  <a name="RequiredPermissions"></a> Необходимые разрешения  
 Использование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зависит от разрешений Windows. Исключение составляет только объект **SQLAgent:Alerts**. Для работы с объектом **SQLAgent:Alerts** пользователь должен быть членом предопределенной роли сервера **sysadmin**.  
  
## <a name="see-also"></a>См. также:  
 [Использование объектов производительности](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
