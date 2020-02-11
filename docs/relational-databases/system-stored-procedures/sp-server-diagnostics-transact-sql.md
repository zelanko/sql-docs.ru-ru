---
title: sp_server_diagnostics (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_server_diagnostics
- sp_server_diagnostics_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_diagnostics
ms.assetid: 62658017-d089-459c-9492-c51e28f60efe
author: stevestein
ms.author: sstein
ms.openlocfilehash: d150d9b027b9a2c4d309ca2055722bb47ba092a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982110"
---
# <a name="sp_server_diagnostics-transact-sql"></a>sp_server_diagnostics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Записывает диагностические данные и сведения о работоспособности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выявления потенциальных неполадок. Процедура работает в повторяющемся режиме и периодически отправляет результаты. Ее можно вызывать из обычного соединения или соединения приложения уровня данных.  
  
**Применимо к** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (и более поздним версиям).  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_server_diagnostics [@repeat_interval =] 'repeat_interval_in_seconds'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @repeat_interval = ] 'repeat_interval_in_seconds'`Указывает интервал времени, в течение которого хранимая процедура будет запускаться повторно для отправки сведений о работоспособности.  
  
 *repeat_interval_in_seconds* имеет **тип int** и значение по умолчанию 0. Допустимыми значениями для параметра являются 0 и любые значения, которые больше или равны 5. Чтобы вернуть полные данные, хранимая процедура должна работать не менее 5 секунд. Минимальное значение для выполнения хранимой процедуры в режиме повтора равно 5 секундам.  
  
 Если этот параметр не указан или задано значение 0, то хранимая процедура один раз вернет данные, а затем завершит работу.  
  
 Если указано значение меньше минимального, то процедура вызывает ошибку и не возвращает данные.  
  
 Если указано значение, большее или равное 5, то хранимая процедура будет повторно выполняться, чтобы возвращать состояние работоспособности, пока не будет отменена вручную.  
  
## <a name="return-code-values"></a>Значения кода возврата  
0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
**sp_server_diagnostics** возвращает следующие сведения.  
  
|Столбец|Тип данных|Description|  
|------------|---------------|-----------------|  
|**creation_time**|**datetime**|Указывает отметку времени создания строки. Все строки в одном наборе данных имеют одинаковые отметки времени.|  
|**component_type**|**имеет sysname**|Указывает, содержит ли строка сведения для компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уровня экземпляра или для Always on группы доступности:<br /><br /> instance<br /><br /> Always On: AvailabilityGroup|  
|**component_name**|**имеет sysname**|Указывает имя компонента или имя группы доступности:<br /><br /> система<br /><br /> resource<br /><br /> query_processing<br /><br /> io_subsystem<br /><br /> events<br /><br /> *\<имя группы доступности>*|  
|**state**|**int**|Указывает состояние работоспособности компонента:<br /><br /> 0<br /><br /> 1<br /><br /> 2<br /><br /> 3|  
|**state_desc**|**имеет sysname**|Описывает столбец state. Далее представлены описания, соответствующие значениям в столбце state:<br /><br /> 0: неизвестно<br /><br /> 1: чистая очистка<br /><br /> 2: предупреждение<br /><br /> 3: ошибка|  
|**data**|**varchar (max)**|Указывает данные, свойственные данному компоненту.|  
  
 Далее даны описания пяти компонентов.  
  
-   **система**: собирает данные с точки зрения системы на спин-блокировки, серьезные условия обработки, нестандартные задачи, ошибки страниц и загрузку ЦП. Эти сведения представляют общие рекомендации по состоянию работоспособности.  
  
-   **ресурс**: собирает данные с точки зрения ресурса для физической и виртуальной памяти, буферных пулов, страниц, кэша и других объектов памяти. Эти сведения представляют рекомендации по состоянию работоспособности.  
  
-   **query_processing**: собирает данные из перспективы обработки запросов в рабочих потоках, задачах, типах ожидания, сеансах с ИНТЕНСИВНЫМ использованием ЦП и блокирующих задачах. Эти сведения представляют рекомендации по состоянию работоспособности.  
  
-   **io_subsystem**: собирает данные по операциям ввода-вывода. Помимо диагностических данных, этот компонент передает состояние удовлетворительной работоспособности или предупреждение работоспособности только для подсистемы ввода-вывода.  
  
-   **события**: собирает данные и поверхности с помощью хранимой процедуры в отношении ошибок и событий, которые записываются сервером, включая сведения об исключениях кольцевого буфера, событиях кольцевого буфера о брокере памяти, нехватке памяти, мониторе планировщиков, буферном пуле, спин-блокировки, безопасности и подключении. В качестве состояния событий всегда указывается 0.  
  
-   имя группы доступности>: собирает данные для указанной группы доступности (если component_type = "Always On: AvailabilityGroup"). ** \< **  
  
## <a name="remarks"></a>Remarks  
Компоненты system, resource и query_processing используются для обнаружения ошибок, а компоненты io_subsystem и events используются только для диагностики.  
  
В следующей таблице представлены компоненты и связанные с ними состояния работоспособности.  
  
|Components|Удовлетворительно (1)|Предупреждение (2)|Ошибка (3)|Неизвестно (0)|  
|----------------|-----------------|-------------------|-----------------|--------------------|  
|система|x|x|x||  
|resource|x|x|x||  
|query_processing|x|x|x||  
|io_subsystem|x|x|||  
|events||||x|  
  
Символ (x) в каждой строке представляет допустимые состояния исправности для компонента. Например, в компоненте io_subsystem показывается удовлетворительное состояние или предупреждение, а ошибки не показываются.  
 
> [!NOTE]
> Выполнение внутренней процедуры sp_server_diagnostics реализуется в потоке с вытеснением с высоким приоритетом.
  
## <a name="permissions"></a>Разрешения  
необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
Рекомендуется использовать расширенные сеансы для записи сведения о работоспособности и записывать их в файл, расположенный вне SQL Server. Это позволит сохранить доступ к файлу в случае сбоя. В следующем примере выходные данные сеанса событий сохраняются в файл:  
```sql  
CREATE EVENT SESSION [diag]  
ON SERVER  
           ADD EVENT [sp_server_diagnostics_component_result] (set collect_data=1)  
           ADD TARGET [asynchronous_file_target] (set filename='c:\temp\diag.xel');  
GO  
ALTER EVENT SESSION [diag]  
      ON SERVER STATE = start;  
GO  
```  
  
В следующем примере запроса считывается файл журнала расширенного сеанса:  
```sql  
SELECT  
    xml_data.value('(/event/@name)[1]','varchar(max)') AS Name  
  , xml_data.value('(/event/@package)[1]', 'varchar(max)') AS Package  
  , xml_data.value('(/event/@timestamp)[1]', 'datetime') AS 'Time'  
  , xml_data.value('(/event/data[@name=''component_type'']/value)[1]','sysname') AS Sysname  
  , xml_data.value('(/event/data[@name=''component_name'']/value)[1]','sysname') AS Component  
  , xml_data.value('(/event/data[@name=''state'']/value)[1]','int') AS State  
  , xml_data.value('(/event/data[@name=''state_desc'']/value)[1]','sysname') AS State_desc  
  , xml_data.query('(/event/data[@name="data"]/value/*)') AS Data  
FROM   
(  
      SELECT  
                        object_name as event  
                        ,CONVERT(xml, event_data) as xml_data  
       FROM    
      sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log\*.xel', NULL, NULL, NULL)  
)   
AS XEventData  
ORDER BY time;  
```  
  
В следующем примере выходные данные процедуры sp_server_diagnostics записываются в таблице в режиме без повторения:  
```sql  
CREATE TABLE SpServerDiagnosticsResult  
(  
      create_time DateTime,  
      component_type sysname,  
      component_name sysname,  
      state int,  
      state_desc sysname,  
      data xml  
);  
INSERT INTO SpServerDiagnosticsResult  
EXEC sp_server_diagnostics; 
```  

В примере запроса ниже считываются сводные выходные значения из таблицы:  
```sql  
SELECT create_time,
       component_name,
       state_desc 
FROM SpServerDiagnosticsResult;  
``` 

В примере запроса ниже считываются некоторые подробные выходные сведения из каждого компонента в таблице:  
```sql  
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult 
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult 
where component_name like 'resource'
go

-- Nonpreemptive waits
select waits.evt.value('(@waitType)','varchar(100)') as 'Wait_Type',
   waits.evt.value('(@waits)','bigint') as 'Waits',
   waits.evt.value('(@averageWaitTime)','bigint') as 'Avg_Wait_Time',
   waits.evt.value('(@maxWaitTime)','bigint') as 'Max_Wait_Time'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/topWaits/nonPreemptive/byDuration/wait') AS waits(evt)
where component_name like 'query_processing'
go

-- Preemptive waits
select waits.evt.value('(@waitType)','varchar(100)') as 'Wait_Type',
   waits.evt.value('(@waits)','bigint') as 'Waits',
   waits.evt.value('(@averageWaitTime)','bigint') as 'Avg_Wait_Time',
   waits.evt.value('(@maxWaitTime)','bigint') as 'Max_Wait_Time'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/topWaits/preemptive/byDuration/wait') AS waits(evt)
where component_name like 'query_processing'
go

-- CPU intensive requests
select cpureq.evt.value('(@sessionId)','bigint') as 'SessionID',
   cpureq.evt.value('(@command)','varchar(100)') as 'Command',
   cpureq.evt.value('(@cpuUtilization)','bigint') as 'CPU_Utilization',
   cpureq.evt.value('(@cpuTimeMs)','bigint') as 'CPU_Time_ms'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/cpuIntensiveRequests/request') AS cpureq(evt)
where component_name like 'query_processing'
go

-- Blocked Process Report
select blk.evt.query('.') as 'Blocked_Process_Report_XML'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/queryProcessing/blockingTasks/blocked-process-report') AS blk(evt)
where component_name like 'query_processing'
go

-- IO
select data.value('(/ioSubsystem/@ioLatchTimeouts)[1]','bigint') as 'Latch_Timeouts',
   data.value('(/ioSubsystem/@totalLongIos)[1]','bigint') as 'Total_Long_IOs'
from SpServerDiagnosticsResult 
where component_name like 'io_subsystem'
go

-- Event information
select xevts.evt.value('(@name)','varchar(100)') as 'xEvent_Name',
   xevts.evt.value('(@package)','varchar(100)') as 'Package',
   xevts.evt.value('(@timestamp)','datetime') as 'xEvent_Time',
   xevts.evt.query('.') as 'Event Data'
from SpServerDiagnosticsResult 
    CROSS APPLY data.nodes('/events/session/RingBufferTarget/event') AS xevts(evt)
where component_name like 'events'
go  
``` 
  
## <a name="see-also"></a>См. также:  
 [Политика отработки отказа для экземпляров отказоустойчивого кластера](../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
