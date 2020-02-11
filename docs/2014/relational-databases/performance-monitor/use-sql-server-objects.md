---
title: Использование объектов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 67edebf9b4adcf40c12190446997dbd7c4b6e57b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63151176"
---
# <a name="use-sql-server-objects"></a>Использование объектов SQL Server
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут использоваться системным монитором для мониторинга активности на компьютере, где запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Объект представляет собой любой ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например блокировку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или процесс Windows. В каждом объекте содержатся один или более счетчиков, определяющих различные аспекты объектов для мониторинга. Например, объект **Блокировки SQL Server** содержит счетчики с названием **Количество взаимоблокировок/с** и **Превышений времени ожидания блокировки в секунду**.  
  
 В некоторых объектах содержится несколько экземпляров разных ресурсов данного типа, существующих на компьютере. Например, у типа объектов **Процессор** будет несколько экземпляров, если в системе установлено несколько процессоров. У типа объектов **Базы данных** будет по одному экземпляру для каждой базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. У некоторых типов объектов (например, у объекта **Диспетчер памяти** ) может быть только один экземпляр. Если у типа объектов несколько экземпляров, можно добавлять счетчики для отслеживания статистики каждого экземпляра или, во многих случаях, для всех экземпляров сразу. Счетчики для экземпляра по умолчанию отображаются в формате **SQLServer:** _\<имя_объекта>_ . Счетчики для именованных экземпляров отображаются в формате **MSSQL$** _\<имя_экземпляра>_ **:** _\<имя_счетчика>_ или **SQLAgent$** _\<имя_экземпляра>_ **:** _\<имя_счетчика>_ .  
  
 Добавляя или удаляя счетчики в диаграмму и сохраняя ее параметры, можно указать объекты и счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которых будут считываться данные при запуске системного монитора.  
  
 Можно настроить системный монитор для отображения статистики любого счетчика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, можно задать пороговое значение для любого счетчика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и затем формировать предупреждение о превышении порога. Дополнительные сведения о настройке предупреждения см. в разделе [Создание предупреждения для базы данных SQL Server](create-a-sql-server-database-alert.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Статистика отображается только при установке экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При остановке и повторном запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отображение статистик прерывается и возобновляется автоматически. Также обратите внимание, что счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] видны в оснастке системного монитора, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущен. На кластеризованном экземпляре счетчики производительности функционируют только на том узле, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [агент SQL Server объектов производительности](#SQLServerAgentPOs)  
  
-   [Service Broker объектов производительности](#ServiceBrokerPOs)  
  
-   [SQL Server объектов производительности](#SQLServerPOs)  
  
-   [Репликация SQL Server объектов производительности](#SQLServerReplicationPOs)  
  
-   [Счетчики конвейера служб SSIS](#SsisPipelineCounters)  
  
-   [Необходимые разрешения](#RequiredPermissions)  
  
##  <a name="SQLServerAgentPOs"></a>агент SQL Server объектов производительности  
 Следующая таблица содержит список объектов измерения производительности для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|[А: оповещения](sql-server-agent-alerts-object.md)|Предоставляет сведения о предупреждениях агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLAgent:Jobs](sql-server-agent-jobs-object.md)|Предоставляет сведения о заданиях агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[А: JobSteps](sql-server-agent-jobsteps-object.md)|Предоставляет сведения о шагах заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Кадр: Статистика](sql-server-agent-statistics-object.md)|Предоставляет общие сведения об агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
##  <a name="ServiceBrokerPOs"></a>Service Broker объектов производительности  
 Следующая таблица содержит список объектов измерения производительности для компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|[SQLServer: Активация компонента Broker](sql-server-broker-activation-object.md)|Предоставляет сведения об активированных задачах компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|[SQLServer:Broker Statistics](sql-server-broker-statistics-object.md)|Предоставляет общие сведения о компоненте [!INCLUDE[ssSB](../../includes/sssb-md.md)] .|  
|[SQLServer: транспорт компонента Service Broker](sql-server-broker-dbm-transport-object.md)|Предоставляет сведения о сетевой работе компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .|  
  
##  <a name="SQLServerPOs"></a>SQL Server объектов производительности  
 В следующей таблице описаны объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|[SQLServer: методы доступа](sql-server-access-methods-object.md)|Ищет и измеряет выделения ресурсов для объектов баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, число поисков в индексе или число страниц, выделенных для индексов и данных).|  
|[SQLServer:Backup Device](sql-server-backup-device-object.md)|Предоставляет сведения об устройствах резервного копирования, использующихся в операциях резервного копирования и восстановления, например пропускную способность устройства.|  
|[SQLServer: Buffer Manager](sql-server-buffer-manager-object.md)|Предоставляет сведения о буферах памяти, использующихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например **свободная память** и **коэффициент попадания в кэш буфера**.|  
|[SQL Server:Buffer Node](sql-server-buffer-node.md)|Предоставляет сведения о том, как часто [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрашивает и получает доступ к свободным страницам.|  
|[SQLServer: CLR](sql-server-clr-object.md)|Предоставляет сведения о языке среды выполнения CLR.|  
|[SQLServer: диспетчер курсоров по типу](sql-server-cursor-manager-by-type-object.md)|Предоставляет сведения о курсорах.|  
|[SQLServer:Cursor Manager Total](sql-server-cursor-manager-total-object.md)|Предоставляет сведения о курсорах.|  
|[SQLServer:Database Mirroring](sql-server-database-mirroring-object.md)|Предоставляет сведения о зеркальном отображении баз данных.|  
|[SQLServer: базы данных](sql-server-databases-object.md)|Предоставляет сведения о базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например объем доступного свободного места для журналов или количество активных транзакций в базе данных. Может существовать несколько экземпляров этого объекта.|  
|[SQL Server: устаревшие функции](sql-server-deprecated-features-object.md)|Подсчитывает частоту использования устаревших функций.|  
|[SQLServer: Exec, статистика](sql-server-execstatistics-object.md)|Предоставляет сведения о статистике выполнения.|  
|[SQLServer: General Statistics](sql-server-general-statistics-object.md)|Предоставляет сведения об активности сервера в общем, например количество пользователей, подключенных к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQL Server: Реплика доступности HADR](sql-server-availability-replica.md)|Предоставляет сведения о репликах доступности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .|  
|[SQL Server: HADR реплика базы данных](sql-server-database-replica.md)|Содержит сведения о репликах базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .|  
|[SQLServer:Latches](sql-server-latches-object.md)|Предоставляет сведения о кратковременных блокировках внутренних ресурсов, например страниц баз данных, использующихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQLServer:Locks](sql-server-locks-object.md)|Предоставляет сведения об отдельных запросах на блокировку, сделанных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например время ожидания блокировки и взаимоблокировки. Может существовать несколько экземпляров этого объекта.|  
|[SQLServer:Memory Manager](sql-server-memory-manager-object.md)|Предоставляет сведения об использовании памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например общее число выделенных на данный момент структур блокировок.|  
|[SQLServer:Plan Cache](sql-server-plan-cache-object.md)|Предоставляет сведения о кэше [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующемся для хранения таких объектов, как хранимые процедуры, триггеры и планы запросов.|  
|[SQLServer: Статистика пула ресурсов](sql-server-resource-pool-stats-object.md)|Предоставляет статистические данные о пуле ресурсов регулятора ресурсов.|  
|[SQLServer:SQL Errors](sql-server-sql-errors-object.md)|Предоставляет сведения об ошибках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[SQLServer:SQL Statistics](sql-server-sql-statistics-object.md)|Предоставляет сведения о разных аспектах запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] , например число пакетов инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , полученных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQLServer: транзакции](sql-server-transactions-object.md)|Предоставляет сведения об активных транзакциях в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например общее число транзакций и число транзакций моментальных снимков.|  
|[SQLServer: пользователь, устанавливаемый](sql-server-user-settable-object.md)|Выполняет пользовательское наблюдение. Каждый счетчик может быть пользовательской хранимой процедурой или любой инструкцией [!INCLUDE[tsql](../../includes/tsql-md.md)] , возвращающей значение, которое можно отслеживать.|  
|[SQLServer: статистика ожидания](sql-server-wait-statistics-object.md)|Предоставляет сведения об ожиданиях.|  
|[SQLServer: статистика группы рабочей нагрузки](sql-server-workload-group-stats-object.md)|Предоставляет статистические данные о группе рабочей нагрузки регулятора ресурсов.|  
  
##  <a name="SQLServerReplicationPOs"></a>Репликация SQL Server объектов производительности  
 Следующая таблица содержит список объектов измерения производительности репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Description|  
|------------------------|-----------------|  
|**SQLServer: агенты репликации**<br /><br /> **SQLServer: моментальный снимок репликации**<br /><br /> **SQLServer: модуль чтения журнала репликации**<br /><br /> **SQLServer: распространитель репликации.**<br /><br /> **SQLServer: слияние репликации**<br /><br /> Дополнительные сведения см. в статье [Monitoring Replication with System Monitor](../replication/monitor/monitoring-replication-with-system-monitor.md).|Содержит сведения о действиях агента репликации.|  
  
##  <a name="SsisPipelineCounters"></a>Счетчики конвейера служб SSIS  
 Сведения о счетчике **Конвейер служб SSIS** см. в разделе [Счетчики производительности](../../integration-services/performance/performance-counters.md).  
  
##  <a name="RequiredPermissions"></a>Необходимые разрешения  
 Использование объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зависит от разрешений Windows. Исключение составляет только объект **SQLAgent:Alerts**. Для работы с объектом **SQLAgent:Alerts** пользователь должен быть членом предопределенной роли сервера **sysadmin**.  
  
## <a name="see-also"></a>См. также:  
 [Использование объектов производительности](../../ssms/agent/use-performance-objects.md)   
 [sys. dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
