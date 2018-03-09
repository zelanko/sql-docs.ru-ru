---
title: "Средства мониторинга и настройки производительности | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools [SQL Server], monitoring performance
- monitoring server performance [SQL Server], tools
- monitoring performance [SQL Server], tools
- database performance [SQL Server], tools
- tuning databases [SQL Server], tools
- database monitoring [SQL Server], tools
- performance [SQL Server], monitoring tools
- server performance [SQL Server], tools
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5121d6d12b0c009a6463f461204da027f67f16ef
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="performance-monitoring-and-tuning-tools"></a>Средства контроля и настройки производительности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит полный набор средств для наблюдения за событиями в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и настройки физической структуры баз данных. Выбор средств зависит от типа контроля или настройки, а также от конкретных отслеживаемых событий.  
  
 Ниже приведены средства контроля и настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Инструмент|Description|  
|----------|-----------------|  
|[sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отслеживает события процесса ядра, например запуск пакета или транзакции, позволяя отслеживать работу сервера и базы данных (взаимоблокировки, неустранимые ошибки, вход в систему). Данные [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно поместить в файл или таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для последующего анализа. Кроме того, предусмотрено пошаговое воспроизведение событий в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для точного определения хода событий.|  
|[Распределенное воспроизведение SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Распределенное воспроизведение позволяет использовать несколько компьютеров для воспроизведения данных трассировки и моделирования ответственной рабочей нагрузки.|  
|[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)|Системный монитор в первую очередь отслеживает использование ресурсов, например количество используемых запросов страниц диспетчера буферов, позволяя отслеживать работу и производительность сервера с помощью предопределенных объектов и счетчиков или пользовательских счетчиков. Системный монитор (монитор производительности в Microsoft Windows NT 4.0) собирает счетчики и показатели, а не данные о событиях (например использование памяти, число активных транзакций, количество блокировок или загрузку ЦП). Для счетчиков можно задавать пороговые значения, при превышении которых операторы будут получать соответствующие уведомления.<br /><br /> Системный монитор работает в операционных системах Microsoft Windows Server и Windows. Он может отслеживать (удаленно или локально) работу экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполняющегося в ОС Windows NT 4.0 или более поздних версий.<br /><br /> Основное отличие между приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и системным монитором состоит в том, что приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отслеживает события ядра СУБД, тогда как системный монитор отслеживает использование ресурсов, связанных с процессами сервера.|  
|[Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|Монитор активности в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет создавать динамические представления текущей активности и наглядно отображать сведения по таким аспектам:<br /><br /> процессы, запущенные на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];<br /><br /> заблокированные процессы;<br /><br /> блокировки;<br /><br /> пользовательскую активность.|  
|[Динамическая статистика запросов](../../relational-databases/performance/live-query-statistics.md)|Отображает статистические данные об этапах выполнения запроса в режиме реального времени. Эти данные доступны в режиме реального времени, поэтому статистика выполнения чрезвычайно полезна для отладки проблем с производительностью запросов.|  
|[Трассировка SQL](../../relational-databases/sql-trace/sql-trace.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] Хранимые процедуры, создающие, фильтрующие и определяющие трассировку:<br /><br /> [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)<br /><br /> [Хранимая процедура sp_trace_generateevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)<br /><br /> [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)<br /><br /> [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)<br /><br /> [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|  
|Журналы ошибок|Журнал событий приложений Windows отражает общую картину событий, происходящих в операционной системе Windows Server или Windows как в едином целом, событий в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и предоставляет полнотекстовый поиск. Сведения о событиях в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны только в этом журнале. Данные журнала ошибок можно использовать для устранения неполадок, связанных с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)|Приведенные ниже системные хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] являются мощной альтернативой для многих задач мониторинга.<br /><br /> [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md):<br />                    Предоставляет сведения моментального снимка о текущих пользователях и процессах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая выполняемые инструкции и их блокировку.<br /><br /> [sp_lock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md):<br />                    Предоставляет сведения моментального снимка о блокировках, включая идентификаторы объекта и индекса, тип блокировки и тип блокируемого ресурса.<br /><br /> [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md): <br />                    Отображает оценку количества места на диске, занятого таблицей (или базой данных).<br /><br /> [sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md):<br />                    отображает статистику, включая загрузку ЦП, использование ввода-вывода и время простоя с момента последнего запуска процедуры **sp_monitor** .|  
|[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)|Инструкции консоли базы данных (DBCC) позволяют просматривать статистику производительности, а также логическую и физическую согласованность базы данных.|  
|[Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)|Встроенные функции отображают статистику моментального снимка по активности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента запуска сервера. Эта статистика хранится в предопределенных счетчиках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, счетчик **@@CPU_BUSY** содержит количество времени, затраченное процессором на выполнение кода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], счетчик **@@CONNECTIONS** — число соединений или попыток соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а **@@PACKET_ERRORS** — количество сетевых пакетов, переданных в соединениях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)|Флаги трассировки отображают сведения об определенных видах деятельности внутри сервера и используются для диагностики неполадок или причин недостаточной производительности (например при цепочках взаимоблокировок).|  
|[помощник по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md)|Помощник по настройке ядра СУБД анализирует то, как инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые применяются к настраиваемым базам данных, воздействуют на производительность. Помощник по настройке ядра СУБД дает рекомендации по добавлению, удалению и изменению индексов, индексированных представлений и секционирования.|  
  
## <a name="choosing-a-monitoring-tool"></a>Выбор средства контроля  
 Выбор средства мониторинга зависит от события или вида деятельности, которые нужно отслеживать.  
  
|Событие или вид деятельности|Приложение SQL Server Profiler|Распределенное воспроизведение|Системный монитор|Монитор активности|Transact-SQL|Журналы ошибок|  
|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Анализ трендов|Да||Да||||  
|Воспроизведение записанных событий|Да (с одного компьютера)|Да (с нескольких компьютеров)|||||  
|Нерегламентированный мониторинг|Да|||Да|Да|Да|  
|Формирование предупреждений|||Да||||  
|Графический интерфейс|Да||Да|Да||Да|  
|Применение в пользовательских приложениях|Да*||||Да||  
  
 *Использование системных хранимых процедур [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .  
  
## <a name="windows-monitoring-tools"></a>Средства контроля Windows  
 Кроме того, в операционных системах Windows и Windows Server 2003 имеются следующие средства наблюдения:  
  
|Инструмент|Description|  
|----------|-----------------|  
|Диспетчер задач|Отображает краткий обзор процессов и приложений, запущенных в системе.|  
|Агент мониторинга сети|Отслеживает сетевой трафик.|  
  
 Дополнительные сведения об операционных системах Windows и Windows Server см. в документации Windows.  
  
  
