---
title: Мониторинг скриптов Python и R с помощью расширенных событий
description: Узнайте, как использовать расширенные события для отслеживания и устранения неполадок, связанных с SQL Server Службы машинного обучения, панель запуска SQL Server, а также внешними скриптами для заданий Python и R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6faef1bd78b1c1aa42714da75679dc989f0b9da9
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714388"
---
# <a name="monitor-python-and-r-scripts-with-extended-events-in-sql-server-machine-learning-services"></a>Мониторинг скриптов Python и R с помощью расширенных событий в SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Узнайте, как использовать расширенные события для отслеживания и устранения неполадок, связанных с SQL Server Службы машинного обучения, панель запуска SQL Server, а также внешними скриптами для заданий Python и R.

## <a name="extended-events-for-sql-server-machine-learning-services"></a>Расширенные события для SQL Server Службы машинного обучения

Чтобы просмотреть список событий, связанных с SQL Server Службы машинного обучения, выполните следующий запрос из Azure Data Studio или SQL Server Management Studio.

```sql
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

Дополнительные сведения об использовании расширенных событий см. в разделе [средства расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).

## <a name="additional-events-specific-to-machine-learning-services"></a>Дополнительные события, относящиеся к Службы машинного обучения

Дополнительные расширенные события доступны для компонентов, которые связаны и используются SQL Server Службы машинного обучения, например [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] и BXLServer, а также вспомогательный процесс, который запускает среду выполнения Python или R. Эти дополнительные расширенные события запускаются из внешних процессов. Поэтому они должны быть захвачены с помощью внешней программы.

Дополнительные сведения о том, как это сделать, см. в разделе [сбор событий из внешних процессов](#bkmk_externalevents).

<a name="bkmk_xeventtable"></a> 

## <a name="table-of-extended-events"></a>Таблица расширенных событий

|Событие|Описание|Примечания|  
|-----------|-----------------|---------|  
|connection_accept|Происходит при принятии нового подключения. Это событие регистрирует все попытки подключения.||  
|failed_launching|Сбой при запуске.|Указывает на ошибку.|  
|satellite_abort_connection|Прерывание записи подключения.||  
|satellite_abort_received|Возникает при получении сообщения о прерывании по вспомогательному соединению.||  
|satellite_abort_sent|Возникает при отправке сообщения о прерывании по вспомогательному соединению.||  
|satellite_authentication_completion|Возникает при завершении проверки подлинности для подключения по протоколу TCP или с помощью канала Namedpipe.||  
|satellite_authorization_completion|Возникает при завершении авторизации для подключения по протоколу TCP или с помощью канала Namedpipe.||  
|satellite_cleanup|Возникает, если вспомогательное подключение вызывает очистку.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_data_chunk_sent|Возникает при завершении отправки одного блока данных по вспомогательному соединению.|Событие сообщает о количестве отправленных строк, количестве столбцов, количестве использованных пакетов SNI и затраченном времени в миллисекундах при отправке блока. Эти сведения помогут вам понять, сколько времени потрачено при передаче различных типов данных и сколько пакетов использовано.|  
|satellite_data_receive_completion|Возникает при получении необходимых данных по запросу через вспомогательное соединение.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_data_send_completion|Возникает при отправке необходимых данных для сеанса через вспомогательное соединение.||  
|satellite_data_send_start|Вызывается при запуске передачи данных.| Передача данных начинается непосредственно перед отправкой первого фрагмента данных.|  
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
|satellite_sessionId_mismatch|Идентификатор сеанса сообщения не ожидается||  

<a name="bkmk_externalevents"></a>

### <a name="collecting-events-from-external-processes"></a>Сбор событий из внешних процессов

SQL Server Службы машинного обучения запускает некоторые службы, работающие за пределами SQL Server процесса. Чтобы записать события, связанные с этими внешними процессами, необходимо создать файл конфигурации трассировки событий и поместить его в тот же каталог, где находится исполняемый файл для процесса.  
  
+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    Чтобы фиксировать события, связанные с панелью запуска, поместите файл конфигурации (*CONFIG*) в каталог Binn экземпляра SQL Server. При установке по умолчанию это будет следующее:

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
+ **BXLServer** — это вспомогательный процесс, который поддерживает расширяемость SQL с использованием внешних языков скриптов, таких как R или Python. Для каждого экземпляра внешнего языка запускается отдельный экземпляр BxlServer.
  
    Чтобы записать события, связанные с BXLServer, поместите файл *config* в каталог установки R или Python. При установке по умолчанию это будет следующее:
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  

    **Python:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`.

Файл конфигурации должен иметь имя, совпадающее с именем исполняемого файла, используя формат "[имя]. XEvents. XML". Другими словами, имя файла должно выглядеть следующим образом:

+ `Launchpad.xevents.xml`
+ `bxlserver.xevents.xml`

Файл конфигурации имеет следующий формат:

```xml
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

+ Чтобы настроить трассировку, измените заполнитель *имени сеанса* , заполнитель для имени файла (`[SessionName].xel`) и имена событий `[XEvent Name 1]`, которые требуется записать, например `[XEvent Name 1]`,).  
+ Может появиться любое количество тегов пакета событий, и они будут собраны при условии, что атрибут Name задан правильно.

### <a name="example-capturing-launchpad-events"></a>Пример Запись событий панели запуска

В следующем примере показано определение трассировки событий для службы панели запуска.

```xml
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

+ Поместите файл *конфигурации* в каталог Binn экземпляра SQL Server.
+ Этот файл должен иметь имя `Launchpad.xevents.xml`.

### <a name="example-capturing-bxlserver-events"></a>Пример Запись событий BXLServer  

В следующем примере представлено определение трассировки событий для исполняемого файла BXLServer.
  
```xml
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

+ Поместите файл *конфигурации* в тот же каталог, в котором находится исполняемый файл BXLServer.
+ Этот файл должен иметь имя `bxlserver.xevents.xml`.

## <a name="next-steps"></a>Следующие шаги

- [Мониторинг выполнения скриптов Python и R с помощью пользовательских отчетов в SQL Server Management Studio](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
- [Мониторинг SQL Server Службы машинного обучения с помощью динамических административных представлений](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
