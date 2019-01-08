---
title: Расширенные события для наблюдения за процессами R и Python - службы машинного обучения SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: aefc4fd3ba5fa1ba69e8e29575037f5e7ac6789a
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644883"
---
# <a name="extended-events-for-sql-server-machine-learning-services"></a>Расширенные события для службы машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server предоставляет набор расширенных событий для разрешения операций, связанных с [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], а также Python или R заданиях, отправленных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

**Применимо к:**  Службы R SQL Server 2016, SQL Server 2017 службы машинного обучения

## <a name="sql-server-events-for-machine-learning"></a>События SQL Server для машинного обучения

Чтобы просмотреть список событий, связанных с SQL Server, запустите запрос, приведенный ниже, из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

```sql
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

Общие сведения об использовании расширенных событий см. в разделе [средства расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).

> [!TIP]
> Для расширенных событий, созданные SQL Server, воспользуйтесь новым [SSMS XEvent profiler](https://docs.microsoft.com/sql/relational-databases/extended-events/use-the-ssms-xe-profiler). Эта новая функция в Management Studio отображает динамические средства просмотра для расширенных событий и меньше вмешивается в SQL Server, чем аналогичные трассировки Profiler.

## <a name="additional-events-specific-to-machine-learning-components"></a>Дополнительные события, относящиеся к компонентов машинного обучения

Доступны дополнительные расширенные события для компонентов, связанных с и использовать службы для машинного обучения SQL Server, такие как [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]и BXLServer, вспомогательный процесс, который запускает среду выполнения R. Эти дополнительные расширенные события запускаются из внешних процессов и таким образом необходимо захватить с помощью внешняя программа.

Дополнительные сведения о том, как это сделать, см. в разделе разделе [сбора событий из внешних процессов](#bkmk_externalevents).

##  <a name="bkmk_xeventtable"></a> Таблица расширенных событий

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
|satellite_data_chunk_sent|Возникает при завершении отправки одного блока данных по вспомогательному соединению.|При отправке фрагмента данных событие сообщает число строк, столбцов, пакетов SNI usedm и затраченное время в миллисекундах. Эти сведения помогут вам понять, сколько времени потрачено при передаче различных типов данных и сколько пакетов использовано.|  
|satellite_data_receive_completion|Возникает при получении необходимых данных по запросу через вспомогательное соединение.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_data_send_completion|Возникает при отправке необходимых данных для сеанса через вспомогательное соединение.||  
|satellite_data_send_start|Возникает при запуске передачи данных.| Передача данных начинается непосредственно перед отправкой первого блока данных.|  
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
  
###  <a name="bkmk_externalevents"></a> Сбор событий из внешних процессов

Службы машинного обучения SQL Server запускают некоторые службы, которые выполняются вне процесса SQL Server. Чтобы фиксировать события, связанные с этими внешними процессами, необходимо создать файл конфигурации трассировки событий и поместите файл в том же каталоге, что и исполняемый файл для процесса.  
  
+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    Чтобы фиксировать события, связанные с панелью запуска, поместите файл конфигурации (*CONFIG*) в каталог Binn экземпляра SQL Server.  При установке по умолчанию будет следующим:

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
+ **BXLServer** — это вспомогательный процесс, который поддерживает возможность расширения SQL с языками внешних скриптов, например R или Python. Для каждого экземпляра внешним языком, который будет запущен отдельный экземпляр BxlServer.
  
    Чтобы фиксировать события, связанные с BXLServer, поместите *.config* файл в каталоге установки R или Python.  При установке по умолчанию будет следующим:
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  

    **Python:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`.

Файл конфигурации должен совпадать с именем исполняемый файл, в формате «[имя].xevents.xml». Другими словами, имя файла должно выглядеть следующим образом:

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

+ Чтобы настроить трассировку, измените *имя сеанса* , заполнитель для имени файла (`[SessionName].xel`) и имена событий, которые вы хотите собирать, например, `[XEvent Name 1]`, `[XEvent Name 1]`).  
+ Любое количество тегов пакет событий может появиться и будут собираться при условии, что атрибут имени правильный.

### <a name="example-capturing-launchpad-events"></a>Пример Фиксация событий панели запуска

В следующем примере определение трассировки событий для службы панели запуска:

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
+ Этот файл должен называться `Launchpad.xevents.xml`.

### <a name="example-capturing-bxlserver-events"></a>Пример Фиксация событий BXLServer  

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
+ Этот файл должен называться `bxlserver.xevents.xml`.

## <a name="see-also"></a>См. также

[Пользовательские отчеты Management Studio для служб машинного обучения](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)
