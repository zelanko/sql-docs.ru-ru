---
title: Мониторинг скриптов с использованием расширенных событий
description: Сведения о том, как использовать расширенные события для мониторинга операций, относящихся к службам машинного обучения SQL Server, панели запуска SQL Server и внешним скриптам заданий Python или R, а также устранять связанные с такими операциями неполадки.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 03/04/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 65ede143baab867d77704ce4e776515d5d7d32de
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87110174"
---
# <a name="monitor-python-and-r-scripts-with-extended-events-in-sql-server-machine-learning-services"></a>Мониторинг скриптов Python и R с использованием расширенных событий в службах машинного обучения SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Сведения о том, как использовать расширенные события для мониторинга операций, относящихся к службам машинного обучения SQL Server, панели запуска SQL Server и внешним скриптам заданий Python или R, а также устранять связанные с такими операциями неполадки.

## <a name="extended-events-for-sql-server-machine-learning-services"></a>Расширенные события для служб машинного обучения SQL Server

Чтобы просмотреть список событий, связанных со службами машинного обучения SQL Server, выполните следующий запрос из Azure Data Studio или SQL Server Management Studio.

```sql
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

Дополнительные сведения об использовании расширенных событий см. в статье [Средства расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).

## <a name="additional-events-specific-to-machine-learning-services"></a>Дополнительные события, относящиеся к службам машинного обучения

Дополнительные расширенные события доступны для компонентов, которые связаны со службами машинного обучения SQL Server и используются ими, таких как [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], BXLServer или вспомогательный процесс, запускающий среду выполнения Python или R. Такие дополнительные расширенные события вызываются из внешних процессов и, соответственно, должны записываться внешней служебной программой.

Дополнительные сведения см. в разделе [Сбор событий из внешних процессов](#bkmk_externalevents).

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
|satellite_data_chunk_sent|Возникает при завершении отправки одного блока данных по вспомогательному соединению.|При отправке фрагмента данных событие сообщает число строк, столбцов, использованных пакетов SNI и затраченное время в миллисекундах. Эти сведения помогут вам понять, сколько времени потрачено при передаче различных типов данных и сколько пакетов использовано.|  
|satellite_data_receive_completion|Возникает при получении необходимых данных по запросу через вспомогательное соединение.|Активируется только внешним процессом. См. инструкции по сбору событий из внешних процессов.|  
|satellite_data_send_completion|Возникает при отправке необходимых данных для сеанса через вспомогательное соединение.||  
|satellite_data_send_start|Вызывается при запуске передачи данных| (непосредственно перед отправкой первого блока данных).|  
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

<a name="bkmk_externalevents"></a>

### <a name="collecting-events-from-external-processes"></a>Сбор событий из внешних процессов

Службы машинного обучения SQL Server запускают некоторые службы, которые выполняются вне процесса SQL Server. Чтобы записывать события, связанные с этими внешними процессами, необходимо создать файл конфигурации трассировки событий и поместить его в тот же каталог, в котором находится исполняемый файл для процесса.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!IMPORTANT]
> Начиная с версии SQL Server 2019 механизм изоляции изменился. Поэтому необходимо предоставить соответствующие разрешения для каталога, в котором хранится файл конфигурации трассировки событий. Дополнительные сведения о настройке этих разрешений см. в разделе [Разрешения для файлов программы | SQL Server 2019 в Windows: изменения в изоляции в Службах машинного обучения](../install/sql-server-machine-learning-services-2019.md#file-permissions).
::: moniker-end

+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    Чтобы фиксировать события, связанные с панелью запуска, поместите файл конфигурации (*XML-файл*) в каталог Binn экземпляра SQL Server. При установке по умолчанию это следующий каталог:

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
+ **BXLServer** — это вспомогательный процесс, который поддерживает возможность расширения SQL с помощью внешних языков скриптов, таких как R и Python. Для каждого экземпляра внешнего языка запускается отдельный экземпляр BxlServer.
  
    Чтобы записывать события, связанные с BXLServer, поместите файл конфигурации (*XML-файл*) в установочный каталог R или Python. При установке по умолчанию это следующий каталог:
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  

    **Python:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`.

Имена файла конфигурации и исполняемого файла должны совпадать и записываться в формате [имя].xevents.xml. Другими словами, имя файла должно выглядеть следующим образом:

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

+ Чтобы настроить трассировку, измените заполнитель *session name*, заполнитель для имени файла (`[SessionName].xel`) и имена событий, которые требуется записывать (например, `[XEvent Name 1]`, `[XEvent Name 1]`).  
+ Может появиться любое количество тегов пакетов событий. Все они будут собираться при условии, что атрибут имени правильный.

### <a name="example-capturing-launchpad-events"></a>Пример Запись событий панели запуска

В следующем примере представлено определение трассировки событий для службы панели запуска:

```xml
<?xml version="1.0" encoding="utf-8"?>  
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

+ Поместите *XML-файл* в каталог Binn экземпляра SQL Server.
+ Этот файл должен иметь имя `Launchpad.xevents.xml`.

### <a name="example-capturing-bxlserver-events"></a>Пример Запись событий BXLServer  

В следующем примере представлено определение трассировки событий для исполняемого файла BXLServer.
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
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

+ Поместите *XML-файл* в тот же каталог, в котором находится исполняемый файл BXLServer.
+ Этот файл должен иметь имя `bxlserver.xevents.xml`.

## <a name="next-steps"></a>Дальнейшие действия

- [Мониторинг выполнения скриптов Python и R с помощью пользовательских отчетов в SQL Server Management Studio](../../machine-learning/administration/monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
- [Мониторинг служб машинного обучения SQL Server с помощью динамических административных представлений](../../machine-learning/administration/monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
