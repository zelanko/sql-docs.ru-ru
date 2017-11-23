---
title: "Расширенные события для служб R SQL Server | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 11/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e90e057-aacb-4adc-8da6-64861f4e87df
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b4d65cd2812fea830bbdd7127b8f47569979e94
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="extended-events-for-sql-server-r-services"></a>Расширенные события для служб R SQL Server
  Службы[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] содержат набор расширенных событий, используемых при операциях по устранению неполадок, связанных с [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] , или в заданиях R, отправленных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Чтобы просмотреть список событий, связанных с SQL Server, запустите запрос, приведенный ниже, из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
```  
select o.name as event_name, o.description  
  from sys.dm_xe_objects o  
  join sys.dm_xe_packages p  
    on o.package_guid = p.guid  
 where o.object_type = 'event'  
   and p.name = 'SQLSatellite';  
```  
  
 Однако некоторые дополнительные расширенные события для [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] запускаются только из внешних процессов, например [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]и BXLServer (вспомогательный процесс, который запускает среду выполнения R). Дополнительные сведения о фиксации этих событий см. в статье [Collecting Events from External Processes](#bkmk_externalevents).  
  
 Общие сведения об использовании расширенных событий см. в статье [SQL Server Extended Events Sessions](../../relational-databases/extended-events/sql-server-extended-events-sessions.md).  

  
##  <a name="bkmk_xeventtable"></a> Таблица расширенных событий  
  
|Событие|Описание|Использовать|  
|-----------|-----------------|---------|  
|connection_accept|Происходит при принятии нового подключения. Это событие регистрирует все попытки подключения.||  
|failed_launching|Сбой при запуске.|Указывает на ошибку.|  
|satellite_abort_connection|Прерывание записи подключения.||  
|satellite_abort_received|Возникает при получении сообщения о прерывании по вспомогательному соединению.||  
|satellite_abort_sent|Возникает при отправке сообщения о прерывании по вспомогательному соединению.||  
|satellite_authentication_completion|Возникает при завершении проверки подлинности для подключения по протоколу TCP или с помощью канала Namedpipe.||  
|satellite_authorization_completion|Возникает при завершении авторизации для подключения по протоколу TCP или с помощью канала Namedpipe.||  
|satellite_cleanup|Возникает, если вспомогательное подключение вызывает очистку.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_data_chunk_sent|Возникает при завершении отправки одного блока данных по вспомогательному соединению.|При отправке фрагмента данных событие сообщает число строк, столбцов, пакетов SNI usedm и затраченное время в миллисекундах. Эти сведения помогут вам понять, сколько времени потрачено при передаче различных типов данных и сколько пакетов использовано.|  
|satellite_data_receive_completion|Возникает при получении необходимых данных по запросу через вспомогательное соединение.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_data_send_completion|Возникает при отправке необходимых данных для сеанса через вспомогательное соединение.||  
|satellite_data_send_start|Возникает при запуске передачи данных (непосредственно перед отправкой первого блока данных).||  
|satellite_error|Используется для трассировки ошибок вспомогательного соединения SQL.||  
|satellite_invalid_sized_message|Недопустимый размер сообщения.||  
|satellite_message_coalesced|Используется для трассировки сообщений, объединяющихся на сетевом уровне.||  
|satellite_message_ring_buffer_record|Запись в кольцевом буфере сообщений.||  
|satellite_message_summary|Сводные сведения об обмене сообщениями.||  
|satellite_message_version_mismatch|Поля версии сообщения не совпадают.||  
|satellite_messaging|Используется для трассировки событий при обмене сообщениями (привязка, отмена привязки и т. д.).||  
|satellite_partial_message|Используется для трассировки неполных сообщений на сетевом уровне.||  
|satellite_schema_received|Возникает, если SQL получает сообщение схемы и выполняет его чтение.||  
|satellite_schema_sent|Возникает при отправке сообщения схемы через вспомогательное соединение.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_service_start_posted|Возникает при публикации сообщения о запуске службы на панели запуска.|Это событие содержит идентификатор для нового сеанса и указывает панели запуска на запуск внешнего процесса.|  
|satellite_unexpected_message_received|Возникает при получении непредвиденного сообщения.|Указывает на ошибку.|  
|stack_trace|Возникает при запросе дампа памяти процесса.|Указывает на ошибку.|  
|trace_event|Используется для отслеживания.|Эти события могут содержать сообщения о трассировке SQL Server, панели запуска и внешних процессов. К ним относится вывод в stdout и stderr из кода R.|  
|launchpad_launch_start|Возникает при запуске вспомогательного соединения на панели запуска.|Активируется только на панели запуска. См. инструкции по сбору событий из launchpad.exe.|  
|launchpad_resume_sent|Возникает при запуске вспомогательного соединения и отправке сообщения о возобновлении на SQL Server с панели запуска.|Активируется только на панели запуска. См. инструкции по сбору событий из launchpad.exe.|  
|satellite_data_chunk_sent|Возникает при завершении отправки одного блока данных по вспомогательному соединению.|Содержит сведения о количестве столбцов, строк, пакетов и продолжительности отправки блока данных.|  
|satellite_sessionId_mismatch|Непредвиденный идентификатор сеанса сообщения.||  
  
###  <a name="bkmk_externalevents"></a> Collecting Events from External Processes  
 Службы[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] запускают некоторые службы, которые выполняются вне процесса SQL Server. Чтобы зафиксировать события, связанные с этими внешними процессами, необходимо создать файл конфигурации трассировки событий и поместить его в тот же каталог, в котором находится исполняемый файл для процесса.  
  
-   **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
     Чтобы фиксировать события, связанные с панелью запуска, поместите файл конфигурации (*CONFIG*) в каталог Binn экземпляра SQL Server.  При установке по умолчанию это каталог `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
-   **BXLServer** — это вспомогательный процесс, который поддерживает возможность расширения SQL с помощью языка R и других языков внешних скриптов.  
  
     Чтобы фиксировать события, связанные с BXLServer, поместите файл конфигурации (*CONFIG*) в установочный каталог R.  При установке по умолчанию это каталог `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  
  
> [!IMPORTANT]
>   Имена файла конфигурации и исполняемого файла должны совпадать и записываться в формате [name].xevents.xml. Другими словами, имя файла должно выглядеть следующим образом:  
>   
> - Launchpad.xevents.XML;  
> - bxlserver.xevents.XML.  
  
 Файл конфигурации имеет следующий формат:  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Примечания.**  
  
-   Чтобы настроить трассировку, измените заполнитель *session name*, заполнитель для имени файла (`[SessionName].xel`) и имена событий, которые требуется зафиксировать (например, `[XEvent Name 1]`, `[XEvent Name 1]`).  
  
-   Может появиться любое количество тегов `event package`. Все они будут собираться при условии, что атрибут имени правильный.  
  
### <a name="example-capturing-launchpad-events"></a>Пример. Фиксация событий панели запуска  
 В следующем примере представлено определение трассировки событий для службы панели запуска.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Примечания.**  
  
-   Поместите файл *конфигурации* в каталог Binn экземпляра SQL Server.  
  
-   Этому файлу нужно присвоить имя *Launchpad.xevents.xml*.  
  
### <a name="example-capturing-bxlserver-events"></a>Пример. Фиксация событий BXLServer  
 В следующем примере представлено определение трассировки событий для исполняемого файла BXLServer.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Примечания.**  
  
-   Поместите файл *конфигурации* в тот же каталог, в котором находится исполняемый файл BXLServer.  
  
-   Этому файлу нужно присвоить имя *bxlserver.xevents.xml*.  
  
## <a name="see-also"></a>См. также:
[Пользовательские отчеты Management Studio для служб R](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md)  
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Мониторинг решений R и управление ими](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  
