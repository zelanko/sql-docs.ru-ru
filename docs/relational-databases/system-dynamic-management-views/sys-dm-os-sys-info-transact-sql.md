---
title: sys.dm_os_sys_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_sys_info_TSQL
- dm_os_sys_info
- dm_os_sys_info_TSQL
- sys.dm_os_sys_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_info dynamic management view
- time [SQL Server], instance started
- starting time
ms.assetid: 20f6bc9c-839a-4fa4-b3f3-a6c47d1b69af
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c56eeab15da21b4c202cd217b0df009db1391616
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265673"
---
# <a name="sysdmossysinfo-transact-sql"></a>sys.dm_os_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает разнородный набор полезных сведений о компьютере, а также о ресурсах, доступных для служб [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и используемых ими.  
  
> **ПРИМЕЧАНИЕ.** Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_sys_info**.  
  
|Имя столбца|Тип данных|Описание и заметки о версии |  
|-----------------|---------------|-----------------|  
|**cpu_ticks**|**bigint**|Задает текущий счетчик тактов времени ЦП. Метки времени ЦП поступают от счетчика процессора RDTSC. Это монотонно возрастающее число. Не допускает значения NULL.|  
|**ms_ticks**|**bigint**|Указывает число миллисекунд, прошедших со времени запуска компьютера. Не допускает значения NULL.|  
|**cpu_count**|**int**|Указывает количество логических процессоров в системе. Не допускает значения NULL.|  
|**hyperthread_ratio**|**int**|Указывает количество логических или физических ядер, соответствующих одному физическому пакету процессора. Не допускает значения NULL.|  
|**physical_memory_in_bytes**|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Указывает общий объем физической памяти компьютера. Не допускает значения NULL.|  
|**physical_memory_kb**|**bigint**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает общий объем физической памяти компьютера. Не допускает значения NULL.|  
|**virtual_memory_in_bytes**|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем виртуальной памяти, доступной процессу в пользовательском режиме. Это значение можно использовать для определения того, был ли SQL Server запущен с параметром 3-GB.|  
|**virtual_memory_kb**|**bigint**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает общий объем виртуального адресного пространства, доступного процессу в пользовательском режиме. Не допускает значения NULL.|  
|**bpool_commited**|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Представляет фиксированную физическую память в килобайтах (КБ) в диспетчере памяти. Не включает зарезервированную память в диспетчере памяти. Не допускает значения NULL.|  
|**committed_kb**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Представляет фиксированную физическую память в килобайтах (КБ) в диспетчере памяти. Не включает зарезервированную память в диспетчере памяти. Не допускает значения NULL.|  
|**bpool_commit_target**|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Представляет объем памяти, в килобайтах (КБ), доступный диспетчеру памяти SQL Server.|  
|**committed_target_kb**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Представляет объем памяти, в килобайтах (КБ), доступный диспетчеру памяти SQL Server. Целевой объем вычисляется с помощью разнообразных входных данных, в том числе:<br /><br /> — Текущее состояние системы, включая ее загруженность<br /><br /> -запрошенной текущими процессами памяти<br /><br /> — объем памяти, установленной на компьютере<br /><br /> -параметры конфигурации<br /><br /> Если **committed_target_kb** больше, чем **committed_kb**, диспетчер памяти попытается получить дополнительную память. Если **committed_target_kb** меньше, чем **committed_kb**, диспетчер памяти попытается уменьшить количество зафиксированной памяти. **Committed_target_kb** всегда включает заимствованную и зарезервированную память. Не допускает значения NULL.|  
|**bpool_visible**|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Количество буферов по 8 KБ в буферном пуле, которые непосредственно доступны в виртуальном адресном пространстве процесса. Если расширения AWE не используются, то при получении буферным пулом целевого объема памяти (bpool_committed = bpool_commit_target) значение bpool_visible становится равным значению bpool_committed. Если расширения AWE используются на 32-разрядной версии SQL Server, bpool_visible представляет размер отображаемой сопоставленной памяти AWE, которая используется для доступа к физической памяти, выделенной под буферный пул. Размер отображаемой сопоставленной памяти привязан к адресному пространству процесса, поэтому видимый объем памяти будет меньше, чем фиксированный объем, и в дальнейшем может быть уменьшен внутренними компонентами, которые потребляют память для целей, не связанных со страницами базы данных. Если значение bpool_visible слишком маленькое, есть вероятность получения ошибок нехватки памяти.|  
|**visible_target_kb**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Совпадает со значением **committed_target_kb**. Не допускает значения NULL.|  
|**stack_size_in_bytes**|**int**|Указывает размер стека вызова для каждого потока, созданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**os_quantum**|**bigint**|Представляет такт времени для задач без вытеснения, выраженный в миллисекундах. Квант времени (в секундах) = **os_quantum** / тактовая частота ЦП. Не допускает значения NULL.|  
|**os_error_mode**|**int**|Задает режим ошибки для процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**os_priority_class**|**int**|Указывает класс приоритета для процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Допускает значение NULL.<br /><br /> 32 = нормальный (журнал ошибок будет выдавать сообщение, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинает выполняться с обычной базой приоритетов (= 7)).<br /><br /> 128 = высокий (журнал ошибок будет выдавать сообщение, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется с высокой базой приоритетов  (=13)).<br /><br /> Дополнительные сведения см. в статье [Настройка параметра конфигурации сервера priority boost](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md).|  
|**max_workers_count**|**int**|Представляет максимальное число исполнителей, которые могут быть созданы. Не допускает значения NULL.|  
|**scheduler_count**|**int**|Представляет число пользовательских планировщиков, настроенных при выполнении процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**scheduler_total_count**|**int**|Представляет общее число планировщиков в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**deadlock_monitor_serial_number**|**int**|Указывает идентификатор текущей последовательности монитора взаимоблокировок. Не допускает значения NULL.|  
|**sqlserver_start_time_ms_ticks**|**bigint**|Представляет **ms_tick** номер при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] последнего запуска. Сравнивается с текущим столбцом ms_ticks. Не допускает значения NULL.|  
|**sqlserver_start_time**|**datetime**|Указывает дату и время последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**affinity_type**|**int**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Задает текущий используемый тип привязки процесса к процессорам. Не допускает значения NULL. Дополнительные сведения см. в разделе [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md).<br /><br /> 1 = MANUAL<br /><br /> 2 = AUTO|  
|**affinity_type_desc**|**varchar(60)**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Описывает **affinity_type** столбца. Не допускает значения NULL.<br /><br /> MANUAL = сходство было задано хотя бы для одного ЦП.<br /><br /> AUTO = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может свободно перемещать потоки между процессорами.|  
|**process_kernel_time_ms**|**bigint**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Общее время в миллисекундах, затраченное всеми потоками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме ядра. Это значение может быть больше, чем время одного процессора, поскольку оно включает в себя время всех процессоров сервера. Не допускает значения NULL.|  
|**process_user_time_ms**|**bigint**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Общее время в миллисекундах, затраченное всеми потоками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в пользовательском режиме. Это значение может быть больше, чем время одного процессора, поскольку оно включает в себя время всех процессоров сервера. Не допускает значения NULL.|  
|**time_source**|**int**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает API-интерфейс, который службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют для извлечения реального времени. Не допускает значения NULL.<br /><br /> 0 = QUERY_PERFORMANCE_COUNTER<br /><br /> 1 = MULTIMEDIA_TIMER|  
|**time_source_desc**|**nvarchar(60)**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Описывает **time_source** столбца. Не допускает значения NULL.<br /><br /> QUERY_PERFORMANCE_COUNTER = [QueryPerformanceCounter](https://go.microsoft.com/fwlink/?LinkId=163095) API извлекает реальное время.<br /><br /> MULTIMEDIA_TIMER = [мультимедийного таймера](https://go.microsoft.com/fwlink/?LinkId=163094) API, который извлекает реальное время.|  
|**virtual_machine_type**|**int**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает, выполняется ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виртуальной среде.  Не допускает значения NULL.<br /><br /> 0 = нет<br /><br /> 1 = HYPERVISOR<br /><br /> 2 = OTHER|  
|**virtual_machine_type_desc**|**nvarchar(60)**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Описывает **virtual_machine_type** столбца. Не допускает значения NULL.<br /><br /> NONE = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущена на виртуальной машине.<br /><br /> HYPERVISOR = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется внутри гипервизора, который подразумевает виртуализацию с поддержкой аппаратного обеспечения. При установке роли Hyper_V низкоуровневая оболочка размещает операционную систему, чтобы экземпляр, запущенный на ОС узла, выполнялся в этой оболочке.<br /><br /> OTHER = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется на виртуальной машине, не использующей поддержку оборудования, например Microsoft Virtual PC.|  
|**softnuma_configuration**|**int**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает, что настроены узлы NUMA способом. Не допускает значения NULL.<br /><br /> 0 = OFF указывает оборудования по умолчанию<br /><br /> 1 = автоматическая архитектура soft-NUMA<br /><br /> 2 = вручную программной архитектуры NUMA с помощью реестра|  
|**softnuma_configuration_desc**|**nvarchar(60)**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> OFF = программной архитектуры NUMA функция — ОТКЛЮЧЕНИЕ<br /><br /> ВКЛЮЧЕН = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определяет размеры узлов NUMA для программной архитектуры NUMA<br /><br /> MANUAL = настроен вручную программной архитектуры NUMA|
|**process_physical_affinity**|**nvarchar(3072)** |**Применимо к:** Начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)].<br /><br />Сведения о еще в будущем. |
|**sql_memory_model**|**int**|**Применимо к:** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Указывает модели памяти, используемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выделения памяти. Не допускает значения NULL.<br /><br />1 = модель обычной памяти<br />2 = блокировка страниц в памяти<br /> 3 = больших страниц в памяти|
|**sql_memory_model_desc**|**nvarchar(120)**|**Применимо к:** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Указывает модели памяти, используемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выделения памяти. Не допускает значения NULL.<br /><br />**ОБЫЧНЫЕ**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует модель обычной памяти для выделения памяти. Это объем памяти sql по умолчанию модель при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы не имеет блокировка страниц в памяти привилегии во время запуска.<br />**LOCK_PAGES**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется блокировка страниц в памяти для выделения памяти. Это диспетчер памяти sql по умолчанию, если учетная запись службы SQL Server должен присутствовать блокировка страниц в памяти во время запуска SQL Server.<br /> **LARGE_PAGES**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использование больших страниц в памяти для выделения памяти. SQL Server использует распределения больших страниц для выделения памяти только в выпуске Enterprise edition, когда учетная запись службы SQL Server должен присутствовать блокировка страниц в памяти во время запуска сервера и при включении трассировки 834 флаг.|
|**pdw_node_id**|**int**|**Применяется к:** [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
|**socket_count** |**int** | **Применимо к:** с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 2 (SP2) по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Указывает количество доступных сокетов процессоров в системе. |  
|**cores_per_socket** |**int** | **Применимо к:** с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 2 (SP2) по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Указывает количество процессоров на ядро, которые доступны в системе. |  
|**numa_node_count** |**int** | **Применимо к:** с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 2 (SP2) по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Указывает количество доступных узлов numa в системе. Этот столбец содержит узлы физической топологией numa, а также узлов программной архитектуры numa. |  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   

## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  



