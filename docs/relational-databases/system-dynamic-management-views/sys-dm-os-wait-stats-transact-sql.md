---
title: sys.dm_os_wait_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/23/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_wait_stats_TSQL
- dm_os_wait_stats
- sys.dm_os_wait_stats
- sys.dm_os_wait_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_wait_stats dynamic management view
ms.assetid: 568d89ed-2c96-4795-8a0c-2f3e375081da
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 513b85aafb4cd25d55dfb40e37dabd6fc47b814f
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878197"
---
# <a name="sysdmoswaitstats-transact-sql"></a>sys.dm_os_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает данные обо всех случаях ожидания, обнаруженных выполнявшимися потоками. Это агрегированное представление можно использовать для диагностики проблем производительности как всего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и конкретных запросов и пакетов. [sys.dm_exec_session_wait_stats &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md) предоставляет аналогичные сведения в сеансе.  
  
> [!NOTE] 
> Вызывать его из **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]**, используйте имя **sys.dm_pdw_nodes_os_wait_stats**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|wait_type|**nvarchar(60)**|Имя типа ожидания. Дополнительные сведения см. в разделе [типы случаев ожидания](#WaitTypes)далее в этом разделе.|  
|waiting_tasks_count|**bigint**|Число ожиданий данного типа. Этот счетчик наращивается каждый раз при начале ожидания.|  
|wait_time_ms|**bigint**|Общее время ожидания данного типа в миллисекундах. Это время включает в себя время signal_wait_time_ms.|  
|max_wait_time_ms|**bigint**|Максимальное время ожидания данного типа.|  
|signal_wait_time_ms|**bigint**|Разница между временем сигнализации ожидающего потока и временем начала его выполнения.|  
|pdw_node_id|**int**|Идентификатор для узла, это распределение является на. <br/> **Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] |  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

##  <a name="WaitTypes"></a> Типы ожиданий  
 **Ожидающие ресурсы** Ожидание ресурсов имеет место, когда исполнитель запрашивает доступ к ресурсу, который недоступен, так как ресурс уже используется другим исполнителем или пока недоступен. Примерами ожидания ресурсов являются блокировки, кратковременные блокировки, сетевые ожидания и ожидания дискового ввода-вывода. Ожидания блокировок и кратковременных блокировок представляют собой ожидания объектов синхронизации.  
  
**Ожиданий в очереди**  
 Ожидание очереди имеет место, когда исполнитель простаивает, ожидая назначения работы. Ожидания очередей чаще всего наблюдаются в системных фоновых задачах, таких как мониторинг взаимоблокировок или очистка удаленных записей. Такие задачи будут ожидать размещения запросов работы в рабочей очереди. Ожидания очередей могут также периодически становиться активными, даже если в очередь не помещались новые пакеты.  
  
 **Внешние ожидания**  
 Внешнее ожидание имеет место, когда исполнитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает завершения внешнего события, например вызова расширенной хранимой процедуры или запроса к связанному серверу. При диагностике критических препятствий следует помнить, что внешние ожидания не всегда означают простой исполнителя, так как этот поток может в данный момент выполнять какой-либо внешний код.  
  
 Представление `sys.dm_os_wait_stats` отображает время выполненных ожиданий. Текущие ожидания в этом динамическом административном представлении не отображаются.  
  
 Исполнитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не считается ожидающим при выполнении любого из следующих условий.  
  
-   Ресурс становится доступным.  
  
-   Очередь не является пустой.  
  
-   Завершается внешний процесс.  
  
 Хотя поток больше не находится в ожидании, он необязательно будет запущен немедленно. Дело в том, что такой поток сначала помещается в очередь работоспособных исполнителей и должен ожидать такта для запуска по расписанию.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] счетчики времени ожидания **bigint** значений и поэтому не вероятно, как переполнение соответствующих счетчиков в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Значения времени конкретных типов ожиданий в процессе выполнения запроса могут указывать на узкие места или точки простоя в запросе. Подобным образом высокие значения времени ожидания или числа ожиданий по всему серверу могут указывать на узкие места или пробки во взаимодействии запросов на экземпляре сервера. Например, ожидания, связанные с блокировкой, указывают на состязание запросов на данные; ожидания, связанные с кратковременными блокировками ввода-вывода страниц, — на медленные значения времени ответа ввода-вывода; ожидания, связанные с кратковременными блокировками обновления страниц, указывают на неверную файловую структуру.  
  
 Содержимое данного динамического административного представления можно очистить, запустив следующую команду.  
  
```sql  
DBCC SQLPERF ('sys.dm_os_wait_stats', CLEAR);  
GO  
```  
  
Эта команда сбрасывает все счетчики на 0.  
  
> [!NOTE]
> Данная статистика не сохраняется при перезапуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и все данные накапливаются с момента последнего сброса статистики или перезапуска сервера.  
  
 В следующей таблице перечислены типы ожиданий, с которыми могут сталкиваться задачи.  

|Тип |Описание| 
|-------------------------- |--------------------------| 
|ABR |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| | 
|AM_INDBUILD_ALLOCATION |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|AM_SCHEMAMGR_UNSHARED_CACHE |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ASSEMBLY_FILTER_HASHTABLE |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ASSEMBLY_LOAD |Имеет место при монопольном доступе к загрузке сборки.| 
|ASYNC_DISKPOOL_LOCK |Имеет место при попытке синхронизации параллельных потоков, выполняющих такие задачи, как создание или инициализация файла.| 
|ASYNC_IO_COMPLETION |Имеет место, когда для своего завершения задача ожидает ввода-вывода.| 
|ASYNC_NETWORK_IO |Имеет место при операциях сетевой записи, когда задача блокируется из сети. Убедитесь, что клиент обрабатывает данные с сервера.| 
|ASYNC_OP_COMPLETION |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ASYNC_OP_CONTEXT_READ |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ASYNC_OP_CONTEXT_WRITE |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ASYNC_SOCKETDUP_IO |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|AUDIT_GROUPCACHE_LOCK |Имеет место, когда возникает ожидание блокировки, которая управляет доступом к определенному кэшу. Кэш содержит сведения о том, какие аудиты используются для слежения за каждой группой действий аудита.| 
|AUDIT_LOGINCACHE_LOCK |Имеет место, когда возникает ожидание блокировки, которая управляет доступом к определенному кэшу. Кэш содержит сведения о том, какие аудиты используются для аудита входа за группами действий аудита.| 
|AUDIT_ON_DEMAND_TARGET_LOCK |Имеет место, когда существует ожидание блокировки, используемой для обеспечения одиночной инициализации связанных с аудитом целей расширенного события.| 
|AUDIT_XE_SESSION_MGR |Имеет место, когда существует ожидание блокировки, используемой для синхронизации запуска и остановки, связанных с аудитом сеансов расширенного события.| 
|BACKUP |Имеет место, когда задача блокируется как часть процесса резервного копирования.| 
|BACKUP_OPERATOR |Имеет место при ожидании задачей монтирования ленты. Для просмотра состояния ленты, запрос sys.dm_io_backup_tapes. Если операция монтирования не назначена к выполнению, этот тип ожидания может указывать на аппаратную проблему накопителя на магнитной ленте.| 
|BACKUPBUFFER |Имеет место при ожидании задачей резервного копирования данных или буфера для их записи. Этот тип встречается редко, преимущественно при ожидании задачей монтирования магнитной ленты.| 
|BACKUPIO |Имеет место при ожидании задачей резервного копирования данных или буфера для их записи. Этот тип встречается редко, преимущественно при ожидании задачей монтирования магнитной ленты.| 
|BACKUPTHREAD |Имеет место, когда для своего завершения задача ожидает завершения задачи резервного копирования. Время ожидания может быть длительным, от нескольких минут до нескольких часов. Если задача, выполнение которой ожидается, находится в процессе ввода-вывода, этот тип не указывает на проблему.| 
|BAD_PAGE_PROCESS |Имеет место, когда фоновый регистратор сбойных страниц пытается избежать запуска чаще, чем каждые пять секунд. Чрезмерное количество сбойных страниц вызывает частые запуски регистратора.| 
|BLOB_METADATA |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BMPALLOCATION |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BMPBUILD |TBD <br />**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BMPREPARTITION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BMPREPLICATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BPSORT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_CONNECTION_RECEIVE_TASK |Имеет место при ожидании доступа для получения сообщения на конечной точке соединения. Доступ на получение к конечной точке сериализуется.| 
|BROKER_DISPATCHER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_ENDPOINT_STATE_MUTEX |Происходит при конфликте доступа к состоянию конечной точки соединения компонента Service Broker. Доступ к состоянию изменений сериализуется.| 
|BROKER_EVENTHANDLER |Происходит, когда задача ожидает в первичном обработчике событий компонента Service Broker. Это должно длиться очень короткое время.| 
|BROKER_FORWARDER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_INIT |Происходит при инициализации компонента Service Broker в каждой активной базы данных. Это не должно происходить часто.| 
|BROKER_MASTERSTART |Происходит, когда задача ожидает для первичного обработчика событий компонента Service Broker для запуска. Это должно длиться очень короткое время.| 
|BROKER_RECEIVE_WAITFOR |Имеет место при ожидании RECEIVE WAITFOR. Это может означать, что сообщения не готовы для получения в очереди или конфликт блокировки не позволяет получать сообщения из очереди.| 
|BROKER_REGISTERALLENDPOINTS |Происходит во время инициализации конечной точки соединения компонента Service Broker. Это должно длиться очень короткое время.| 
|BROKER_SERVICE |Происходит, когда обновляется или упразднены компонента Service Broker целевой список, который связан с целевой службой.| 
|BROKER_SHUTDOWN |Имеет место при запланированном завершении работы компонента Service Broker. Это ожидание обычно длится короткое время, если вообще имеет место.| 
|BROKER_START |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_TASK_SHUTDOWN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_TASK_STOP |Происходит, когда обработчик задачи очереди компонента Service Broker пытается завершить работу задачи. Проверка состояния сериализуется и заранее должна находиться в выполняющемся состоянии.| 
|BROKER_TASK_SUBMIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_TO_FLUSH |Происходит, когда служба передачи компонента Service Broker отложенной flusher сбросов в памяти объектов в рабочую таблицу.| 
|BROKER_TRANSMISSION_OBJECT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_TRANSMISSION_TABLE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_TRANSMISSION_WORK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|BROKER_TRANSMITTER |Происходит, когда передатчика компонента Service Broker ожидает завершения работы. Компонент Service Broker содержит компонент, известный как передатчика, которая планирует сообщения из нескольких диалогов для отправки по каналу связи через один или несколько конечных точек подключения. Передатчика имеет 2 выделенных потоков для этой цели. Этот тип ожидания начисляется при этих передатчика потоки ожидают диалоговое окно сообщения должны отправляться с помощью транспортных подключений. Высокие значения из waiting_tasks_count для этого типа ожидания периодических работа для этих потоков передатчика и не указывают на проблемы с производительностью. Если компонент service broker не используется вообще, waiting_tasks_count должна быть 2 (для потока передатчика 2), а wait_time_ms дважды время с момента запуска экземпляра. См. в разделе [статистику ожидания компонента Service broker](https://blogs.msdn.microsoft.com/sql_service_broker/2008/12/01/service-broker-wait-types).|
|BUILTIN_HASHKEY_MUTEX |Может иметь место после запуска экземпляра, во время инициализации внутренних структур данных. После инициализации структур данных повторяться не будет.| 
|CHANGE_TRACKING_WAITFORCHANGES |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CHECK_PRINT_RECORD |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|CHECK_SCANNER_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CHECK_TABLES_INITIALIZATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CHECK_TABLES_SINGLE_SCAN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CHECK_TABLES_THREAD_BARRIER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CHECKPOINT_QUEUE |Имеет место при ожидании задачей контрольных точек следующего запроса контрольной точки.| 
|CHKPT |Имеет место при запуске сервера для уведомления потока контрольных точек о возможности его запуска.| 
|CLEAR_DB |Происходит во время операций, которые изменяют состояние базы данных, таких как открытие или закрытие базы данных.| 
|CLR_AUTO_EVENT |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает инициации конкретного автособытия. Ожидание обычно длится долго и не указывает на проблему.| 
|CLR_CRST |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает ввода критической секции задачи, используемой в данный момент другой задачей.| 
|CLR_JOIN |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает завершения другой задачи. Такое состояние ожидания имеет место при соединении задач.| 
|CLR_MANUAL_EVENT |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает инициации конкретного ручного события.| 
|CLR_MEMORY_SPY |Возникает во время ожидания получения блокировки для структуры данных, используемой для записи всех выделений виртуальной памяти, поступающих из среды CLR. Структура данных блокируется для обеспечения ее целостности при осуществлении параллельного доступа.| 
|CLR_MONITOR |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает получения блокировки мониторинга.| 
|CLR_RWLOCK_READER |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает блокировки модуля чтения.| 
|CLR_RWLOCK_WRITER |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает блокировки модуля записи.| 
|CLR_SEMAPHORE |Имеет место, когда задача в данный момент производит выполнение среды CLR и ожидает семафора.| 
|CLR_TASK_START |Имеет место при ожидании задачей CLR выполнения запуска.| 
|CLRHOST_STATE_ACCESS |Имеет место, если происходит ожидание для получения монопольного доступа к структурам данных, на которых размещена среда CLR. Этот тип ожидания происходит при установке или удалении среды выполнения CLR.| 
|CMEMPARTITIONED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CMEMTHREAD |Имеет место, когда задача ожидает объекта памяти, безопасного для использования потоками. Время ожидания может возрасти при состязаниях между несколькими задачами, пытающимися выделить память через один и тот же объект памяти.| 
|COLUMNSTORE_BUILD_THROTTLE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|COLUMNSTORE_COLUMNDATASET_SESSION_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|COMMIT_TABLE |TBD| 
|CONNECTION_ENDPOINT_LOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|COUNTRECOVERYMGR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CREATE_DATINISERVICE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|CXCONSUMER |Происходит с планами параллельных запросов, когда поток-потребитель ожидает поток-производитель для отправки строк. Это является обычной частью параллельного выполнения запросов. <br /> **Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2, [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|
|CXPACKET |Происходит с планами параллельных запросов, при синхронизации итератора обмена обработчика запросов, а также при создании и использовании строк. Если ожидание избыточно и не может быть уменьшено путем настройки запросов (например, добавлением индексов), рассмотрите возможность настройки параметра cost threshold for parallelism или уменьшите степень параллелизма.<br /> **Примечание:** начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2, [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3, и [!INCLUDE[ssSDS](../../includes/sssds-md.md)], ожидания CXPACKET относится только к синхронизации итератора обмена обработчика запросов и создания строк для потоки-потребители. Потоки-потребители в тип ожидания CXCONSUMER отслеживаются отдельно.| 
|CXROWSET_SYNC |Имеет место при параллельном просмотре диапазона.| 
|DAC_INIT |Имеет место при инициализации выделенного административного соединения.| 
|DBCC_SCALE_OUT_EXPR_CACHE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DBMIRROR_DBM_EVENT |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|DBMIRROR_DBM_MUTEX |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|DBMIRROR_EVENTS_QUEUE |Имеет место при ожидании обработки событий в процессе зеркального отображения базы данных.| 
|DBMIRROR_SEND |Имеет место, когда задача ожидает очистки резервного журнала коммуникаций сетевого уровня для получения возможности отправки сообщений. Указывает на начало переполнения уровня коммуникаций, что повлияет на пропускную способность зеркального отображения базы данных.| 
|DBMIRROR_WORKER_QUEUE |Указывает, что рабочая задача зеркального отображения базы данных ожидает дальнейшей работы.| 
|DBMIRRORING_CMD |Имеет место, когда задача ожидает сохранения записей журнала на диск. Это состояние ожидания обычно занимает длительные периоды времени.| 
|DBSEEDING_FLOWCONTROL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DBSEEDING_OPERATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DEADLOCK_ENUM_MUTEX |Происходит, когда монитор взаимоблокировок и представление sys.dm_os_waiting_tasks пытаются удостовериться, что SQL Server не выполняется несколько операций поиска взаимоблокировок одновременно.| 
|DEADLOCK_TASK_SEARCH |Большое время ожидания этого ресурса указывает на то, что сервер выполняет запросы в верхней части представления sys.dm_os_waiting_tasks и что эти запросы блокируют поиск взаимоблокировок монитором взаимоблокировок. Такой тип ожидания используется только монитором взаимоблокировки. Запросы в верхней части представления sys.dm_os_waiting_tasks используют ожидание DEADLOCK_ENUM_MUTEX.| 
|DEBUG |Происходит во время Transact-SQL и CLR, отладка для внутренней синхронизации.| 
|DIRECTLOGCONSUMER_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DIRTY_PAGE_POLL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DIRTY_PAGE_SYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DIRTY_PAGE_TABLE_LOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DISABLE_VERSIONING |Происходит, когда SQL Server опрашивает диспетчер транзакции версий, чтобы увидеть, является ли метка времени самой ранней активной транзакции более поздней версии, чем отметка времени начала изменения состояния. При этом варианте все транзакции моментальных снимков, запущенные до запуска инструкции ALTER DATABASE, завершаются. Это состояние ожидания используется в том случае, когда SQL Server отключает управление версиями с помощью инструкции ALTER DATABASE.| 
|DISKIO_SUSPEND |Имеет место, когда задача ожидает доступа к файлу при активном внешнем резервном копировании. Это регистрируется для каждого ожидающего пользовательского процесса. Значение, большее 5 на один пользовательский процесс, может указывать на то, что внешнее резервное копирование занимает слишком много времени.| 
|DISPATCHER_PRIORITY_QUEUE_SEMAPHORE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DISPATCHER_QUEUE_SEMAPHORE |Имеет место, когда поток из пула диспетчеров ожидает поступления дополнительной работы. Время ожидания данного типа ожидания увеличится, если диспетчер находится в состоянии простоя.| 
|DLL_LOADING_MUTEX |Имеет место один раз при ожидании загрузки DLL-библиотеки синтаксического анализатора XML.| 
|DPT_ENTRY_LOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DROP_DATABASE_TIMER_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DROPTEMP |Имеет место между попытками удаления временного объекта, если предыдущая попытка закончилась неудачно. Длительность ожидания растет экспоненциально с каждой неудачной попыткой удаления.| 
|DTC |Имеет место, когда задача ожидает события, используемого для управления переходом состояний. Это состояние контролирует, когда происходит восстановление транзакций координатора распределенных транзакций Microsoft (MS DTC), после того как SQL Server получает уведомление о недоступности службы MS DTC.| 
|DTC_ABORT_REQUEST |Имеет место в течение сеанса исполнителя службы MS DTC, когда сеанс ожидает получения владения транзакцией MS DTC. После получения службой MS DTC владения транзакцией сеанс может произвести ее откат. В общем случае сеанс будет ожидать другого сеанса, использующего транзакцию.| 
|DTC_RESOLVE |Имеет место, когда в ходе транзакции между базами данных задача восстановления ожидает базу данных master, чтобы запросить результат транзакции.| 
|DTC_STATE |Имеет место, когда задача ожидает события, защищающего изменения внутреннего объекта глобального состояния службы MS DTC. Это состояние должно держаться в течение очень короткого промежутка времени.| 
|DTC_TMDOWN_REQUEST |Происходит в сеансе рабочих MS DTC, когда SQL Server получает уведомление, что служба MS DTC не доступна. Сначала исполнитель ждет начала процесса восстановления MS DTC. Затем он ждет получения результата распределенной транзакции, над которой он работал. Это может продолжаться до тех пор, пока соединение со службой MS DTC не будет восстановлено.| 
|DTC_WAITFOR_OUTCOME |Имеет место, когда задачи восстановления ждут активизации службы MS DTC для получения возможности разрешения подготовленных транзакций.| 
|DTCNEW_ENLIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DTCNEW_PREPARE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DTCNEW_RECOVERY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DTCNEW_TM |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DTCNEW_TRANSACTION_ENLISTMENT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DTCPNTSYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|DUMP_LOG_COORDINATOR |Имеет место, когда главная задача ожидает формирования данных подзадачей. Обычно это состояние не наблюдается. Длительное время ожидания указывает на непредвиденную блокировку. Следует изучить поведение подзадачи.| 
|DUMP_LOG_COORDINATOR_QUEUE |TBD| 
|DUMPTRIGGER |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|EC |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|EE_PMOLOCK |Имеет место в процессе синхронизации определенных типов выделения памяти в ходе выполнения инструкции.| 
|EE_SPECPROC_MAP_INIT |Имеет место в процессе синхронизации создания внутренней хэш-таблицы процедуры. Этот тип ожидания происходит только при первом доступе к хэш-таблице после запуска экземпляра SQL Server.| 
|ENABLE_EMPTY_VERSIONING |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ENABLE_VERSIONING |Происходит, когда SQL Server ожидает завершения всех транзакций обновления базы данных перед объявлением готовности к переходу в разрешенное состояние изоляции моментального снимка базы данных. Это состояние используется в том случае, когда SQL Server разрешает изоляцию моментальных снимков с помощью инструкции ALTER DATABASE.| 
|ERROR_REPORTING_MANAGER |Имеет место в процессе синхронизации нескольких параллельных инициализаций журнала ошибок.| 
|EXCHANGE |Имеет место в процессе синхронизации в итераторе обмена обработчика запросов при параллельных запросах.| 
|EXECSYNC |Имеет место в процессе синхронизации в обработчике запросов в областях, не относящихся к итератору обмена, при параллельных запросах. Примерами таких областей являются битовые карты, большие двоичные объекты (LOB) и итератор подкачки. Это состояние ожидания может часто использоваться объектами LOB.| 
|EXECUTION_PIPE_EVENT_INTERNAL |Имеет место при синхронизации между производителем и потребителем пакетного выполнения, переданных через контекст соединения.| 
|EXTERNAL_RG_UPDATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|EXTERNAL_SCRIPT_NETWORK_IO |TBD <br /> **Применяется к**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до текущей.| 
|EXTERNAL_SCRIPT_PREPARE_SERVICE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|EXTERNAL_SCRIPT_SHUTDOWN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|EXTERNAL_WAIT_ON_LAUNCHER, |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FABRIC_HADR_TRANSPORT_CONNECTION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FABRIC_REPLICA_CONTROLLER_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FABRIC_REPLICA_CONTROLLER_STATE_AND_CONFIG |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FABRIC_REPLICA_PUBLISHER_EVENT_PUBLISH |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FABRIC_REPLICA_PUBLISHER_SUBSCRIBER_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FABRIC_WAIT_FOR_BUILD_REPLICA_EVENT_PROCESSING |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FAILPOINT |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FCB_REPLICA_READ |Имеет место при синхронизации операций чтения разреженного файла моментального снимка (или временного моментального снимка, созданного с помощью DBCC).| 
|FCB_REPLICA_WRITE |Имеет место при синхронизации помещения страницы или запроса страницы из разреженного файла моментального снимка (или временного моментального снимка, созданного с помощью DBCC).| 
|FEATURE_SWITCHES_UPDATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_DB_KILL_FLAG |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_DB_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_FCB |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_FCB_FIND |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_FCB_PARENT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_FCB_RELEASE_CACHED_ENTRIES |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_FCB_STATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_FILEOBJECT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NSO_TABLE_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_NTFS_STORE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_RECOVERY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_RSFX_COMM |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_RSFX_WAIT_FOR_MEMORY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_STARTUP_SHUTDOWN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_STORE_DB |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_STORE_ROWSET_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FFT_STORE_TABLE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILE_VALIDATION_THREADS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILESTREAM_CACHE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILESTREAM_CHUNKER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILESTREAM_CHUNKER_INIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILESTREAM_FCB |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILESTREAM_FILE_OBJECT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILESTREAM_WORKITEM_QUEUE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FILETABLE_SHUTDOWN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FOREIGN_REDO |TBD <br /> **Применяется к**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до текущей.| 
|FORWARDER_TRANSITION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FS_FC_RWLOCK |Имеет место, когда сборщик мусора FILESTREAM ожидает выполнения одного из следующих действий:| 
|FS_GARBAGE_COLLECTOR_SHUTDOWN |Имеет место, если сборщик мусора FILESTREAM ожидает завершения задач очистки.| 
|FS_HEADER_RWLOCK |Имеет место при ожидании получения доступа к заголовку FILESTREAM контейнера данных FILESTREAM с целью считывания или обновления содержимого файла заголовка FILESTREAM (Filestream.hdr).| 
|FS_LOGTRUNC_RWLOCK |Имеет место при ожидании получения доступа к усечению журнала FILESTREAM для выполнения любого из следующих действий.| 
|FSA_FORCE_OWN_XACT |Возникает, если операции ввода-вывода файла FILESTREAM необходимо установить соединение со связанной транзакцией, которая в данный момент занята другим сеансом.| 
|FSAGENT |Имеет место, если операция ввода-вывода файла FILESTREAM ожидает ресурс агента FILESTREAM, используемого операцией ввода-вывода другого файла.| 
|FSTR_CONFIG_MUTEX |Имеет место во время ожидания завершения перенастройки другой функции FILESTREAM.| 
|FSTR_CONFIG_RWLOCK |Имеет место при ожидании сериализации доступа к параметрам конфигурации FILESTREAM.| 
|FT_COMPROWSET_RWLOCK |Полнотекстовая операция ожидает завершения операции фрагментирования метаданных. Документируется исключительно в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FT_IFTS_RWLOCK |Полнотекстовая операция ожидает внутренней синхронизации. Документируется исключительно в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FT_IFTS_SCHEDULER_IDLE_WAIT |Тип ожидания спящего режима планировщика полнотекстовой операции. Планировщик находится в состоянии простоя.| 
|FT_IFTSHC_MUTEX |Полнотекстовая операция ожидает операции управления fdhost. Документируется исключительно в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FT_IFTSISM_MUTEX |Полнотекстовая операция ожидает завершения операции связи. Документируется исключительно в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FT_MASTER_MERGE |Полнотекстовая операция ожидает завершения операции слияния в единый файл. Документируется исключительно в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FT_MASTER_MERGE_COORDINATOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FT_METADATA_MUTEX |Документируется исключительно в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|FT_PROPERTYLIST_CACHE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|FT_RESTART_CRAWL |Имеет место в случае, когда требуется перезапуск полнотекстового сканирования с последней надежной точки для восстановления после временного сбоя. Ожидание позволяет рабочим задачам, работающим в данный момент над этим заполнением, завершиться или завершить текущий этап.| 
|FULLTEXT GATHERER |Имеет место в процессе синхронизации полнотекстовых операций.| 
|GDMA_GET_RESOURCE_OWNER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GHOSTCLEANUP_UPDATE_STATS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GHOSTCLEANUPSYNCMGR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GLOBAL_QUERY_CANCEL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GLOBAL_QUERY_CLOSE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GLOBAL_QUERY_CONSUMER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GLOBAL_QUERY_PRODUCER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GLOBAL_TRAN_CREATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GLOBAL_TRAN_UCS_SESSION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|GUARDIAN |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|HADR_AG_MUTEX |Происходит, когда инструкция языка DDL Always On или команда отказоустойчивой кластеризации Windows Server ожидает монопольного доступа к конфигурации группы доступности., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_AR_CRITICAL_SECTION_ENTRY |Происходит, когда инструкция языка DDL Always On или команда отказоустойчивой кластеризации Windows Server ожидает монопольного доступа к состоянию среды локальной реплики соответствующей группы доступности., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_AR_MANAGER_MUTEX |Возникает в том случае, когда операция завершения работы реплики доступности ожидает окончания запуска либо операция запуска реплики доступности ожидает окончания операции завершения. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_AR_UNLOAD_COMPLETED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_ARCONTROLLER_NOTIFICATIONS_SUBSCRIBER_LIST |Издатель события реплики доступности (например, события изменения состояния или изменения конфигурации) ожидает монопольного доступа к списку подписчиков на событие для чтения и записи. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_BACKUP_BULK_LOCK |Always On базы данных-источника получил запрос резервного копирования из базы данных-получателя и ожидает фона поток завершит обработку запроса на получение или снятие блокировки BulkOp., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_BACKUP_QUEUE |Фоновый поток резервного копирования первичной базы данных AlwaysOn ожидает нового рабочего запроса из базы данных-получателя. (как правило, это происходит, когда база данных-источник содержит журнал BulkOp и ожидает базы данных-получателя указать, что база данных-источник может снять блокировку)., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_CLUSAPI_CALL |Поток SQL Server ожидает переключения из режима без вытеснения (планируемого сервером SQL Server) в режим с вытеснением (запланированное или операционной системой) для вызова интерфейсов API кластеризации Windows Server отработки отказа., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_COMPRESSED_CACHE_SYNC |Ожидание доступа в кэш блоков сжатого журнала, который позволяет предотвратить избыточное сжатие блоков журнала, отправленных для нескольких баз данных-получателей., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_CONNECTIVITY_INFO |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DATABASE_FLOW_CONTROL |Ожидание отправки сообщений участнику, когда количество сообщений в очереди достигло максимума. Означает, что просмотр журнала выполняется быстрее, чем отправка по сети. Это актуально только в том случае, если отправка по сети происходит медленнее, чем ожидалось., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DATABASE_VERSIONING_STATE |Происходит при изменении состояния управления версиями копии базы данных Always On. Этот тип ожидания для внутренних структур данных и обычно оно очень непродолжительно напрямую не влияет на доступ к данным., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DATABASE_WAIT_FOR_RECOVERY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DATABASE_WAIT_FOR_RESTART |Ожидание перезапуска в системе управления группами доступности AlwaysOn базы данных. В обычных условиях это не является проблемой для клиента, так как ожидание здесь предусмотрено., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DATABASE_WAIT_FOR_TRANSITION_TO_VERSIONING |Запрос к объектам в удобном для чтения базы данных-получателя из Always On группы доступности блокируется на управлении версиями строк во время ожидания для фиксации или отката всех транзакций, которые выполнялись, когда была включена вторичная реплика для рабочих нагрузок чтения. Этот тип ожидания гарантирует, что версии строк будут доступны до выполнения запроса в режиме изоляции моментального снимка., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DB_COMMAND |Ожидание ответов на разговорные сообщения (которые требуют явного ответа от другой стороны, используя инфраструктуру разговорных сообщений Always On). Этот тип ожидания используется несколько разных типов сообщений., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DB_OP_COMPLETION_SYNC |Ожидание ответов на разговорные сообщения (которые требуют явного ответа от другой стороны, используя инфраструктуру разговорных сообщений Always On). Этот тип ожидания используется несколько разных типов сообщений., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DB_OP_START_SYNC |Инструкции языка DDL Always On или команда отказоустойчивой кластеризации Windows Server ожидает сериализованного доступа к базе данных доступности и состоянию ее среды., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DBR_SUBSCRIBER |Издатель события реплики доступности (например, события изменения состояния или изменения конфигурации) ожидает монопольного доступа на чтение и запись к состоянию среды подписчика на событие, который соответствует базе данных доступности. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DBR_SUBSCRIBER_FILTER_LIST |Издатель события реплики доступности (например, события изменения состояния или изменения конфигурации) ожидает монопольного доступа на чтение и запись к списку подписчиков на событие, которые соответствуют базе данных доступности. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DBSEEDING |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DBSEEDING_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_DBSTATECHANGE_SYNC |Ожидание управления параллелизмом, обновления внутреннего состояния реплики базы данных., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FABRIC_CALLBACK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_BLOCK_FLUSH |Диспетчер транспорта FILESTREAM Always On ожидает до завершения обработки блока журнала., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_FILE_CLOSE |Диспетчер транспорта FILESTREAM Always On ожидает, пока не обрабатываются следующий файл FILESTREAM и закрыт дескриптор., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_FILE_REQUEST |Always On для первичной реплики для отправки всех запрошенного FILESTREAM ожидает вторичной реплики файлы во время ОТКАТА., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_IOMGR |Диспетчер транспорта FILESTREAM Always On ожидает блокировки чтения/записи, которая защищает диспетчер файлового ПОТОКА всегда на операции ввода-вывода во время запуска и завершения работы., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_IOMGR_IOCOMPLETION |Диспетчер всегда на ввода-вывода FILESTREAM ожидает завершения ввода-вывода., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_MANAGER |Диспетчер транспорта FILESTREAM Always On ожидает блокировки чтения/записи, которая защищает диспетчер транспорта FILESTREAM AlwaysOn в во время запуска и завершения работы., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_FILESTREAM_PREPROC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_GROUP_COMMIT |Механизм обработки фиксации транзакций ожидает, пока будет разрешена групповая фиксация, чтобы поместить несколько записей о фиксации транзакций в один блок журнала. Этот тип ожидания является ожидаемое условие, которое оптимизирует операции ввода-вывода журнала, записи и отправки операций., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_LOGCAPTURE_SYNC |Управление параллелизмом во время записи в журнал или применения объекта при создании или удалении операций просмотра. Это ожидание предусмотрено, когда участники меняют состояние или статус соединения., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_LOGCAPTURE_WAIT |Ожидание момента, когда записи журнала станут доступны. Это может произойти в том случае, если ожидается создание новых записей журнала соединениями или завершение ввода-вывода при чтении журнала, который не находится в кэше. Это ожидание предусмотрено, если просмотра журнала является штатной конца журнала или выполняется чтение с диска., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_LOGPROGRESS_SYNC |Ожидания для управления параллелизмом при обновлении состояния хода выполнения журнала реплик базы данных., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_NOTIFICATION_DEQUEUE |Фоновая задача, которая обрабатывает уведомления WSFC, ожидает следующего уведомления. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_NOTIFICATION_WORKER_EXCLUSIVE_ACCESS |Диспетчер реплики доступности Always On ожидает сериализованного доступа к состоянию среды фоновой задачи, которая обрабатывает уведомления отказоустойчивой кластеризации Windows Server. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_NOTIFICATION_WORKER_STARTUP_SYNC |Фоновая задача ожидает окончания запуска фоновой задачи, которая обрабатывает уведомления WSFC. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_NOTIFICATION_WORKER_TERMINATION_SYNC |Фоновая задача ожидает завершения работы фоновой задачи, которая обрабатывает уведомления WSFC. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_PARTNER_SYNC |Ожидание управления параллелизмом список участников., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_READ_ALL_NETWORKS |Ожидание доступа к списку сетей WSFC для чтения или записи. Только для внутреннего применения. Примечание: Система хранит список сетей WSFC, используемый в динамических административных представлениях (например, sys.dm_hadr_cluster_networks) или для проверки Transact-SQL AlwaysOn инструкций, ссылающихся на WSFC сведения о сети. Этот список обновляется при запуске ядра, связанных с WSFC уведомления и внутренней Always On перезапуска (например, утери и кворума WSFC). Обычно задачи будут блокироваться, пока выполняется обновление в этом списке. , <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_RECOVERY_WAIT_FOR_CONNECTION |Ожидание подключения базы данных-получателя к базе данных-источнику до начала восстановления. Это ожидание предусмотрено, который можно увеличить, при низкой для установления подключения к первичной реплике., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_RECOVERY_WAIT_FOR_UNDO |Механизм восстановления базы данных ожидает, пока база данных-получатель закончит фазу восстановления и инициализации, которая вернет ее к общей временной точке в журнале с базой данных-источником. Это ожидание предусмотрено после отработки отказа. Отменить можно отследить ход выполнения с помощью системного монитора Windows (perfmon.exe) и динамических административных представлений., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_REPLICAINFO_SYNC |Ожидание управления параллелизмом обновление текущего состояния реплики., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SEEDING_CANCELLATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SEEDING_FILE_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SEEDING_LIMIT_BACKUPS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SEEDING_SYNC_COMPLETION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SEEDING_TIMEOUT_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SEEDING_WAIT_FOR_COMPLETION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SYNC_COMMIT |Механизм обработки фиксации транзакций ожидает, пока синхронизированные базы данных-получатели запишут журнал на диск. Это ожидание также отражается в счетчике производительности «Задержка транзакции». Этот тип ожидания ожидается синхронизации группы доступности и указывает время отправки, запись и подтвердить журнала базы данных-получатели., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_SYNCHRONIZING_THROTTLE |Ожидание, пока механизм обработки фиксации транзакции разрешит синхронизацию базы данных-получателя с окончанием журнала базы данных-источника для перехода в синхронизированное состояние. Это ожидание предусмотрено, когда синхронизируется с базой данных-получателем., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_TDS_LISTENER_SYNC |Внутренняя система Always On или кластер WSFC запросит запуск или остановку прослушивателей. Обработка этого запроса всегда выполняется асинхронно, и существует механизм для удаления избыточных запросов. Существуют также моменты, когда этот процесс приостанавливается из-за изменений в конфигурации. Все ожидания, связанные с этим механизмом синхронизации прослушивателей, используют этот тип ожидания. Только для внутреннего использования., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_TDS_LISTENER_SYNC_PROCESSING |Используется в конце инструкции Transact-SQL AlwaysOn, которая требует запуска или остановки прослушивателя anavailability группы. Поскольку операция запуска или остановки выполняется асинхронно, пользовательский поток будет блокировать использовать этот тип ожидания, пока состояние прослушивателя известно., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_THROTTLE_LOG_RATE_GOVERNOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_THROTTLE_LOG_RATE_LOG_SIZE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_THROTTLE_LOG_RATE_SEEDING |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_THROTTLE_LOG_RATE_SEND_RECV_QUEUE_SIZE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_TIMER_TASK |Ожидание получения блокировки на объект задачи таймера. Используется также для реализации фактического ожидания между моментами времени, когда выполняется работа. Например, для задачи, которая выполняется каждые 10 секунд, после одного выполнения групп доступности AlwaysOn ожидает около 10 секунд задачу в расписание, и это ожидание задается здесь., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_TRANSPORT_DBRLIST |Ожидание доступа к списку реплик базы данных транспортного уровня. Используется для спин-блокировки, которая предоставляет доступ к нему., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_TRANSPORT_FLOW_CONTROL |Ожидание, пока число необработанных неподтвержденных сообщений AlwaysOn, находится над out пороговое значение управления потоком. Это на основе реплики для реплики доступности (не на основе базы данных для базы данных)., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_TRANSPORT_SESSION |Группы доступности AlwaysOn ожидает, пока изменение или доступ к базовому состоянию транспорта., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_WORK_POOL |Ожидание управления параллелизмом объект фоновой рабочей задачи группы доступности AlwaysOn., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_WORK_QUEUE |Группы доступности AlwaysOn фоновый рабочий поток, ожидая назначения новой работы. Это ожидание предусмотрено, когда есть готовые рабочие процессы, ожидающие новой работы, который находится в обычном состоянии., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HADR_XRF_STACK_ACCESS |Доступ к (искать, добавлять и удалять) стеку вилок восстановления для базы данных доступности Always On., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HCCO_CACHE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HK_RESTORE_FILEMAP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HKCS_PARALLEL_MIGRATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HKCS_PARALLEL_RECOVERY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HTBUILD |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HTDELETE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HTMEMO |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HTREINIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HTREPARTITION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|HTTP_ENUMERATION |Имеет место при запуске системы для перечисления конечных точек HTTP с целью запуска протокола HTTP.| 
|HTTP_START |Имеет место при ожидании соединением завершения инициализации HTTP.| 
|HTTP_STORAGE_CONNECTION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|IMPPROV_IOWAIT |Происходит, когда SQL Server ожидает завершения ввода-вывода массовой загрузке.| 
|INSTANCE_LOG_RATE_GOVERNOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|INTERNAL_TESTING |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|IO_AUDIT_MUTEX |Имеет место в процессе синхронизации буферов событий трассировки.| 
|IO_COMPLETION |Имеет место при ожидании завершения операций ввода-вывода. Этот тип ожидания обычно не относится к операциям ввода-вывода страниц данных. Ожидания завершения ввода-вывода страниц данных отображаются как PAGEIOLATCH\_ \* ожидает.| 
|IO_QUEUE_LIMIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|IO_RETRY |Имеет место, когда операция ввода-вывода (например, чтение или запись на диск), завершается неудачно в связи с нехваткой ресурсов, после чего производится повторная попытка.| 
|IOAFF_RANGE_QUEUE |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|KSOURCE_WAKEUP |Используется задачей управления службами при ожидании запросов от диспетчера управления службами. Ожидание обычно длится долго и не указывает на проблему.| 
|KTM_ENLISTMENT |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|KTM_RECOVERY_MANAGER |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|KTM_RECOVERY_RESOLUTION |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|LATCH_DT |Имеет место при ожидании кратковременной блокировки DT (удаления). Не включает в себя буферные кратковременные блокировки или кратковременные блокировки меток транзакции. Список кратковременной БЛОКИРОВКИ\_ \* ожиданий доступен в представлении sys.dm_os_latch_stats. Обратите внимание на то, что в представлении sys.dm_os_latch_stats ожидания LATCH_NL, LATCH_SH, LATCH_UP, LATCH_EX и LATCH_DT сгруппированы.| 
|LATCH_EX |Имеет место при ожидании кратковременной блокировки EX (монопольной). Не включает в себя буферные кратковременные блокировки или кратковременные блокировки меток транзакции. Список кратковременной БЛОКИРОВКИ\_ \* ожиданий доступен в представлении sys.dm_os_latch_stats. Обратите внимание на то, что в представлении sys.dm_os_latch_stats ожидания LATCH_NL, LATCH_SH, LATCH_UP, LATCH_EX и LATCH_DT сгруппированы.| 
|LATCH_KP |Имеет место при ожидании кратковременной блокировки KP (удержания). Не включает в себя буферные кратковременные блокировки или кратковременные блокировки меток транзакции. Список кратковременной БЛОКИРОВКИ\_ \* ожиданий доступен в представлении sys.dm_os_latch_stats. Обратите внимание на то, что в представлении sys.dm_os_latch_stats ожидания LATCH_NL, LATCH_SH, LATCH_UP, LATCH_EX и LATCH_DT сгруппированы.| 
|LATCH_NL |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|LATCH_SH |Имеет место при ожидании кратковременной блокировки SH (коллективной). Не включает в себя буферные кратковременные блокировки или кратковременные блокировки меток транзакции. Список кратковременной БЛОКИРОВКИ\_ \* ожиданий доступен в представлении sys.dm_os_latch_stats. Обратите внимание на то, что в представлении sys.dm_os_latch_stats ожидания LATCH_NL, LATCH_SH, LATCH_UP, LATCH_EX и LATCH_DT сгруппированы.| 
|LATCH_UP |Имеет место при ожидании кратковременной блокировки UP (обновления). Не включает в себя буферные кратковременные блокировки или кратковременные блокировки меток транзакции. Список кратковременной БЛОКИРОВКИ\_ \* ожиданий доступен в представлении sys.dm_os_latch_stats. Обратите внимание на то, что в представлении sys.dm_os_latch_stats ожидания LATCH_NL, LATCH_SH, LATCH_UP, LATCH_EX и LATCH_DT сгруппированы.| 
|LAZYWRITER_SLEEP |Имеет место при приостановке задач средства отложенной записи. Представляет собой показатель времени, затраченного ожидающими фоновыми задачами. Не следует учитывать это состояние при исследовании пользовательских простоев.| 
|LCK_M_BU |Имеет место, когда задача ожидает получения блокировки для массового обновления (BU).| 
|LCK_M_BU_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки для массового обновления (BU) с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_BU_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки для массового обновления (BU) с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_IS |Имеет место, когда задача ожидает получения блокировки с намерением коллективного доступа (IS).| 
|LCK_M_IS_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки с намерением коллективного доступа (IS) с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_IS_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки с намерением коллективного доступа (IS) с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_IU |Имеет место, когда задача ожидает получения блокировки с намерением обновления (IU).| 
|LCK_M_IU_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки с намерением обновления (IU) с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_IU_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки с намерением обновления (IU) с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_IX |Имеет место, когда задача ожидает получения блокировки с намерением монопольного доступа (IX).| 
|LCK_M_IX_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки с намерением монопольного доступа (IX) с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_IX_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки с намерением монопольного доступа (IX) с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_NL |Имеет место, когда задача ожидает получения блокировки типа NULL на текущее ключевое значение и блокировки вставки диапазона между текущим и предыдущим ключами. Блокировка типа NULL на ключ — это блокировка с немедленным снятием.| 
|LCK_M_RIn_NL_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки типа NULL с блокаторами аварийного завершения на текущее ключевое значение и блокировки вставки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. Блокировка типа NULL на ключ — это блокировка с немедленным снятием. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_NL_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки типа NULL с низким приоритетом на текущее ключевое значение и блокировки вставки диапазона с низким приоритетом между текущим и предыдущим ключами. Блокировка типа NULL на ключ — это блокировка с немедленным снятием. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_S |Имеет место, когда задача ожидает получения совмещаемой блокировки на текущее ключевое значение и блокировки вставки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RIn_S_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения совмещаемой блокировки с блокаторами аварийного завершения на текущее ключевое значение и блокировки вставки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_S_LOW_PRIORITY |Имеет место, когда задача ожидает получения совмещаемой блокировки с низким приоритетом на текущее ключевое значение и блокировки вставки диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_U |Задача ожидает получения блокировки на обновление текущего ключевого значения и блокировки вставки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RIn_U_ABORT_BLOCKERS |Задача ожидает получения блокировки обновления с блокаторами аварийного завершения на текущее ключевое значение и блокировки вставки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_U_LOW_PRIORITY |Задача ожидает получения блокировки обновления с низким приоритетом на текущее ключевое значение и блокировки вставки диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_X |Имеет место, когда задача ожидает получения монопольной блокировки на текущее ключевое значение и блокировки вставки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RIn_X_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения монопольной блокировки с блокаторами аварийного завершения на текущее ключевое значение и блокировки вставки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RIn_X_LOW_PRIORITY |Имеет место, когда задача ожидает получения монопольной блокировки с низким приоритетом на текущее ключевое значение и блокировки вставки диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RS_S |Имеет место, когда задача ожидает получения совмещаемой блокировки на текущее ключевое значение и совмещаемой блокировки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RS_S_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения совмещаемой блокировки с блокаторами аварийного завершения на текущее ключевое значение и совмещаемой блокировки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RS_S_LOW_PRIORITY |Имеет место, когда задача ожидает получения совмещаемой блокировки с низким приоритетом на текущее ключевое значение и совмещаемой блокировки диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RS_U |Имеет место, когда задача ожидает получения блокировки обновления текущего ключевого значения и блокировки обновления диапазона между текущим и предыдущим ключами.| 
|LCK_M_RS_U_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки обновления с блокаторами аварийного завершения на текущее ключевое значение и блокировки на обновление диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RS_U_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки обновления с низким приоритетом на текущее ключевое значение и блокировки на обновление диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RX_S |Имеет место, когда задача ожидает получения совмещаемой блокировки на текущее ключевое значение и монопольной блокировки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RX_S_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения совмещаемой блокировки с блокаторами аварийного завершения на текущее ключевое значение и монопольной блокировки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RX_S_LOW_PRIORITY |Имеет место, когда задача ожидает получения совмещаемой блокировки с низким приоритетом на текущее ключевое значение и монопольной блокировки с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RX_U |Имеет место, когда задача ожидает получения блокировки на обновление текущего ключевого значения и монопольной блокировки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RX_U_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки обновления с блокаторами аварийного завершения на текущее ключевое значение и монопольной блокировки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RX_U_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки обновления с низким приоритетом на текущее ключевое значение и монопольной блокировки диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RX_X |Имеет место, когда задача ожидает получения монопольной блокировки на текущее ключевое значение и монопольной блокировки диапазона между текущим и предыдущим ключами.| 
|LCK_M_RX_X_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения монопольной блокировки с блокаторами аварийного завершения на текущее ключевое значение и монопольной блокировки диапазона с блокаторами аварийного завершения между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_RX_X_LOW_PRIORITY |Имеет место, когда задача ожидает получения монопольной блокировки с низким приоритетом на текущее ключевое значение и монопольной блокировки диапазона с низким приоритетом между текущим и предыдущим ключами. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_S |Имеет место, когда задача ожидает получения совмещаемой блокировки.| 
|LCK_M_S_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения совмещаемой блокировки с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_S_LOW_PRIORITY |Имеет место, когда задача ожидает получения совмещаемой блокировки с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SCH_M |Имеет место, когда задача ожидает получения блокировки на изменение схемы.| 
|LCK_M_SCH_M_ABORT_BLOCKERS |Возникает, когда задача ожидает получения блокировки на изменение схемы с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SCH_M_LOW_PRIORITY |Возникает, когда задача ожидает получения блокировки на изменение схемы с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SCH_S |Имеет место, когда задача ожидает получения совмещаемой блокировки схемы.| 
|LCK_M_SCH_S_ABORT_BLOCKERS |Возникает, когда задача ожидает получения совмещаемой блокировки схемы с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SCH_S_LOW_PRIORITY |Возникает, когда задача ожидает получения совмещаемой блокировки схемы с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SIU |Имеет место, когда задача ожидает получения совмещаемой блокировки с намерением обновления.| 
|LCK_M_SIU_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения совмещаемой блокировки обновления с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SIU_LOW_PRIORITY |Возникает, когда задача ожидает получения совмещаемой блокировки обновления с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SIX |Имеет место, когда задача ожидает получения совмещаемой блокировки с намерением монопольного доступа.| 
|LCK_M_SIX_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения совмещаемой блокировки с намерением монопольного доступа с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_SIX_LOW_PRIORITY |Возникает, когда задача ожидает получения совмещаемой блокировки с намерением монопольного доступа с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_U |Имеет место, когда задача ожидает получения блокировки на обновление.| 
|LCK_M_U_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки обновления с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_U_LOW_PRIORITY |Имеет место, когда задача ожидает получения блокировки обновления с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_UIX |Имеет место, когда задача ожидает получения блокировки на обновление с намерением монопольного доступа.| 
|LCK_M_UIX_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения блокировки на обновление с намерением монопольного доступа с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_UIX_LOW_PRIORITY |Возникает, когда задача ожидает получения блокировки на обновление с намерением монопольного доступа с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_X |Имеет место, когда задача ожидает получения блокировки на монопольный доступ.| 
|LCK_M_X_ABORT_BLOCKERS |Имеет место, когда задача ожидает получения монопольной блокировки с блокаторами аварийного завершения. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LCK_M_X_LOW_PRIORITY |Имеет место, когда задача ожидает получения монопольной блокировки с низким приоритетом. (Связано с параметром ожидания с низким приоритетом инструкций ALTER TABLE и ALTER INDEX.), <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOG_POOL_SCAN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOG_RATE_GOVERNOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGBUFFER |Имеет место, когда задача ожидает освобождения пространства в буфере журнала для сохранения записи в журнал. Последовательные высокие значения могут указывать на то, что устройства записи в журнал не справляются с объемом записей, формируемых сервером.| 
|LOGCAPTURE_LOGPOOLTRUNCPOINT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGGENERATION |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|LOGMGR |Имеет место, когда задача ожидает завершения каких-либо связанных с журналом внешних операций ввода-вывода перед тем, как закрыть журнал для закрытия базы данных.| 
|LOGMGR_FLUSH |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|LOGMGR_PMM_LOG |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGMGR_QUEUE |Имеет место, когда задача записи в журнал ожидает рабочих запросов.| 
|LOGMGR_RESERVE_APPEND |Имеет место, когда задача ожидает проверки освобождения достаточного пространства для новой записи в журнал после его усечения. Для уменьшения времени этого ожидания попробуйте увеличить размер файлов журнала для затронутой базы данных.| 
|LOGPOOL_CACHESIZE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGPOOL_CONSUMER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGPOOL_CONSUMERSET |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGPOOL_FREEPOOLS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGPOOL_MGRSET |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGPOOL_REPLACEMENTSET |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOGPOOLREFCOUNTEDOBJECT_REFDONE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|LOWFAIL_MEMMGR_QUEUE |Имеет место при ожидании доступности памяти для использования.| 
|MD_AGENT_YIELD |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|MD_LAZYCACHE_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|MEMORY_ALLOCATION_EXT |Происходит при выделении памяти из внутреннего пула памяти SQL Server или в операционной системе., <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|MEMORY_GRANT_UPDATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|METADATA_LAZYCACHE_RWLOCK |TBD <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|MIGRATIONBUFFER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ДОПОЛНИТЕЛЬНО |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|ДОПОЛНИТЕЛЬНО |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|MSQL_DQ |Имеет место, когда задача ожидает завершения операции распределенного запроса. Это используется для выявления потенциальных взаимоблокировок приложений MARS. Ожидание окончится по завершении вызова распределенного запроса.| 
|MSQL_XACT_MGR_MUTEX |Имеет место, когда задача ожидает получения прав на владение диспетчером транзакций сеансов для выполнения транзакционной операции сеансового уровня.| 
|MSQL_XACT_MUTEX |Имеет место в процессе синхронизации использования транзакции. Прежде чем запрос сможет использовать транзакцию, он должен получить объект взаимного исключения.| 
|MSQL_XP |Происходит, когда задание ожидает завершения расширенной хранимой процедуры. Это состояние ожидания используется SQL Server для выявления потенциальных взаимоблокировок приложений MARS. Ожидание окончится по завершении вызова расширенной хранимой процедуры.| 
|MSSEARCH |Имеет место в процессе вызова полнотекстового поиска. Ожидание окончится по завершении операции полнотекстового поиска. Это указывает не на состязание, а на длительность операций полнотекстового поиска.| 
|NET_WAITFOR_PACKET |Имеет место при ожидании соединением сетевого пакета в процессе чтения из сети.| 
|NETWORKSXMLMGRLOAD |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|NODE_CACHE_MUTEX |TBD| 
|OLEDB |Возникает, когда SQL Server вызывает поставщик SQL Server собственного клиента OLE DB. Этот тип ожидания не используется для синхронизации. Он указывает на длительность вызовов поставщика OLE DB.| 
|ONDEMAND_TASK_QUEUE |Имеет место, когда фоновая задача ожидает запросов системных задач с высоким приоритетом. Длительное время ожидания указывает, что к процессу не было высокоприоритетных запросов, и причины для беспокойства нет.| 
|PAGEIOLATCH_DT |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме удаления. Длительное время ожидания может указывать на проблемы с дисковой подсистемой.| 
|PAGEIOLATCH_EX |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в исключительном режиме. Длительное время ожидания может указывать на проблемы с дисковой подсистемой.| 
|PAGEIOLATCH_KP |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме удержания. Длительное время ожидания может указывать на проблемы с дисковой подсистемой.| 
|PAGEIOLATCH_NL |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PAGEIOLATCH_SH |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме общего доступа. Длительное время ожидания может указывать на проблемы с дисковой подсистемой.| 
|PAGEIOLATCH_UP |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме обновления. Длительное время ожидания может указывать на проблемы с дисковой подсистемой.| 
|PAGELATCH_DT |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося не в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме удаления.| 
|PAGELATCH_EX |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося не в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в исключительном режиме.| 
|PAGELATCH_KP |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося не в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме удержания.| 
|PAGELATCH_NL |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PAGELATCH_SH |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося не в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме общего доступа.| 
|PAGELATCH_UP |Имеет место, когда задача ожидает кратковременной блокировки буфера, находящегося не в состоянии запроса ввода-вывода. Запрос на кратковременную блокировку производится в режиме обновления.| 
|PARALLEL_BACKUP_QUEUE |Имеет место при сериализации вывода инструкции RESTORE HEADERONLY, RESTORE FILELISTONLY или RESTORE LABELONLY.| 
|PARALLEL_REDO_DRAIN_WORKER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PARALLEL_REDO_FLOW_CONTROL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PARALLEL_REDO_LOG_CACHE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PARALLEL_REDO_TRAN_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PARALLEL_REDO_TRAN_TURN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PARALLEL_REDO_WORKER_SYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PARALLEL_REDO_WORKER_WAIT_WORK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PERFORMANCE_COUNTERS_RWLOCK |TBD| 
|PHYSICAL_SEEDING_DMV |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|POOL_LOG_RATE_GOVERNOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_ABR |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PREEMPTIVE_AUDIT_ACCESS_EVENTLOG |Происходит, если планировщик операционной системы SQLOS [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] переключается в режим с вытеснением, чтобы записать событие аудита в журнал событий Windows. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|PREEMPTIVE_AUDIT_ACCESS_SECLOG |Происходит, если планировщик SQLOS переключается в режим с вытеснением, чтобы записать событие аудита в журнал безопасности Windows. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|PREEMPTIVE_CLOSEBACKUPMEDIA |Происходит, если планировщик SQLOS переключается в режим с вытеснением, чтобы закрыть носители резервной копии.| 
|PREEMPTIVE_CLOSEBACKUPTAPE |Происходит, если планировщик SQLOS переключается в режим с вытеснением, чтобы закрыть устройство резервного копирования на магнитной ленте.| 
|PREEMPTIVE_CLOSEBACKUPVDIDEVICE |Происходит, если планировщик SQLOS переключается в режим с вытеснением, чтобы закрыть виртуальное устройство резервного копирования.| 
|PREEMPTIVE_CLUSAPI_CLUSTERRESOURCECONTROL |Происходит, если планировщик SQLOS переключается в режим с вытеснением, чтобы выполнить операции отказоустойчивого кластера Windows.| 
|PREEMPTIVE_COM_COCREATEINSTANCE |Происходит, если планировщик SQLOS переключается в режим с вытеснением, чтобы создать COM-объект.| 
|PREEMPTIVE_COM_COGETCLASSOBJECT |TBD| 
|PREEMPTIVE_COM_CREATEACCESSOR |TBD| 
|PREEMPTIVE_COM_DELETEROWS |TBD| 
|PREEMPTIVE_COM_GETCOMMANDTEXT |TBD| 
|PREEMPTIVE_COM_GETDATA |TBD| 
|PREEMPTIVE_COM_GETNEXTROWS |TBD| 
|PREEMPTIVE_COM_GETRESULT |TBD| 
|PREEMPTIVE_COM_GETROWSBYBOOKMARK |TBD| 
|PREEMPTIVE_COM_LBFLUSH |TBD| 
|PREEMPTIVE_COM_LBLOCKREGION |TBD| 
|PREEMPTIVE_COM_LBREADAT |TBD| 
|PREEMPTIVE_COM_LBSETSIZE |TBD| 
|PREEMPTIVE_COM_LBSTAT |TBD| 
|PREEMPTIVE_COM_LBUNLOCKREGION |TBD| 
|PREEMPTIVE_COM_LBWRITEAT |TBD| 
|PREEMPTIVE_COM_QUERYINTERFACE |TBD| 
|PREEMPTIVE_COM_RELEASE |TBD| 
|PREEMPTIVE_COM_RELEASEACCESSOR |TBD| 
|PREEMPTIVE_COM_RELEASEROWS |TBD| 
|PREEMPTIVE_COM_RELEASESESSION |TBD| 
|PREEMPTIVE_COM_RESTARTPOSITION |TBD| 
|PREEMPTIVE_COM_SEQSTRMREAD |TBD| 
|PREEMPTIVE_COM_SEQSTRMREADANDWRITE |TBD| 
|PREEMPTIVE_COM_SETDATAFAILURE |TBD| 
|PREEMPTIVE_COM_SETPARAMETERINFO |TBD| 
|PREEMPTIVE_COM_SETPARAMETERPROPERTIES |TBD| 
|PREEMPTIVE_COM_STRMLOCKREGION |TBD| 
|PREEMPTIVE_COM_STRMSEEKANDREAD |TBD| 
|PREEMPTIVE_COM_STRMSEEKANDWRITE |TBD| 
|PREEMPTIVE_COM_STRMSETSIZE |TBD| 
|PREEMPTIVE_COM_STRMSTAT |TBD| 
|PREEMPTIVE_COM_STRMUNLOCKREGION |TBD| 
|PREEMPTIVE_CONSOLEWRITE |TBD| 
|PREEMPTIVE_CREATEPARAM |TBD| 
|PREEMPTIVE_DEBUG |TBD| 
|PREEMPTIVE_DFSADDLINK |TBD| 
|PREEMPTIVE_DFSLINKEXISTCHECK |TBD| 
|PREEMPTIVE_DFSLINKHEALTHCHECK |TBD| 
|PREEMPTIVE_DFSREMOVELINK |TBD| 
|PREEMPTIVE_DFSREMOVEROOT |TBD| 
|PREEMPTIVE_DFSROOTFOLDERCHECK |TBD| 
|PREEMPTIVE_DFSROOTINIT |TBD| 
|PREEMPTIVE_DFSROOTSHARECHECK |TBD| 
|PREEMPTIVE_DTC_ABORT |TBD| 
|PREEMPTIVE_DTC_ABORTREQUESTDONE |TBD| 
|PREEMPTIVE_DTC_BEGINTRANSACTION |TBD| 
|PREEMPTIVE_DTC_COMMITREQUESTDONE |TBD| 
|PREEMPTIVE_DTC_ENLIST |TBD| 
|PREEMPTIVE_DTC_PREPAREREQUESTDONE |TBD| 
|PREEMPTIVE_FILESIZEGET |TBD| 
|PREEMPTIVE_FSAOLEDB_ABORTTRANSACTION |TBD| 
|PREEMPTIVE_FSAOLEDB_COMMITTRANSACTION |TBD| 
|PREEMPTIVE_FSAOLEDB_STARTTRANSACTION |TBD| 
|PREEMPTIVE_FSRECOVER_UNCONDITIONALUNDO |TBD| 
|PREEMPTIVE_GETRMINFO |TBD| 
|PREEMPTIVE_HADR_LEASE_MECHANISM |Планирование для диагностики CSS диспетчера аренды групп доступности AlwaysOn., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_HTTP_EVENT_WAIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_HTTP_REQUEST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_LOCKMONITOR |TBD| 
|PREEMPTIVE_MSS_RELEASE |TBD| 
|PREEMPTIVE_ODBCOPS |TBD| 
|PREEMPTIVE_OLE_UNINIT |TBD| 
|PREEMPTIVE_OLEDB_ABORTORCOMMITTRAN |TBD| 
|PREEMPTIVE_OLEDB_ABORTTRAN |TBD| 
|PREEMPTIVE_OLEDB_GETDATASOURCE |TBD| 
|PREEMPTIVE_OLEDB_GETLITERALINFO |TBD| 
|PREEMPTIVE_OLEDB_GETPROPERTIES |TBD| 
|PREEMPTIVE_OLEDB_GETPROPERTYINFO |TBD| 
|PREEMPTIVE_OLEDB_GETSCHEMALOCK |TBD| 
|PREEMPTIVE_OLEDB_JOINTRANSACTION |TBD| 
|PREEMPTIVE_OLEDB_RELEASE |TBD| 
|PREEMPTIVE_OLEDB_SETPROPERTIES |TBD| 
|PREEMPTIVE_OLEDBOPS |TBD| 
|PREEMPTIVE_OS_ACCEPTSECURITYCONTEXT |TBD| 
|PREEMPTIVE_OS_ACQUIRECREDENTIALSHANDLE |TBD| 
|PREEMPTIVE_OS_AUTHENTICATIONOPS |TBD| 
|PREEMPTIVE_OS_AUTHORIZATIONOPS |TBD| 
|PREEMPTIVE_OS_AUTHZGETINFORMATIONFROMCONTEXT |TBD| 
|PREEMPTIVE_OS_AUTHZINITIALIZECONTEXTFROMSID |TBD| 
|PREEMPTIVE_OS_AUTHZINITIALIZERESOURCEMANAGER |TBD| 
|PREEMPTIVE_OS_BACKUPREAD |TBD| 
|PREEMPTIVE_OS_CLOSEHANDLE |TBD| 
|PREEMPTIVE_OS_CLUSTEROPS |TBD| 
|PREEMPTIVE_OS_COMOPS |TBD| 
|PREEMPTIVE_OS_COMPLETEAUTHTOKEN |TBD| 
|PREEMPTIVE_OS_COPYFILE |TBD| 
|PREEMPTIVE_OS_CREATEDIRECTORY |TBD| 
|PREEMPTIVE_OS_CREATEFILE |TBD| 
|PREEMPTIVE_OS_CRYPTACQUIRECONTEXT |TBD| 
|PREEMPTIVE_OS_CRYPTIMPORTKEY |TBD| 
|PREEMPTIVE_OS_CRYPTOPS |TBD| 
|PREEMPTIVE_OS_DECRYPTMESSAGE |TBD| 
|PREEMPTIVE_OS_DELETEFILE |TBD| 
|PREEMPTIVE_OS_DELETESECURITYCONTEXT |TBD| 
|PREEMPTIVE_OS_DEVICEIOCONTROL |TBD| 
|PREEMPTIVE_OS_DEVICEOPS |TBD| 
|PREEMPTIVE_OS_DIRSVC_NETWORKOPS |TBD| 
|PREEMPTIVE_OS_DISCONNECTNAMEDPIPE |TBD| 
|PREEMPTIVE_OS_DOMAINSERVICESOPS |TBD| 
|PREEMPTIVE_OS_DSGETDCNAME |TBD| 
|PREEMPTIVE_OS_DTCOPS |TBD| 
|PREEMPTIVE_OS_ENCRYPTMESSAGE |TBD| 
|PREEMPTIVE_OS_FILEOPS |TBD| 
|PREEMPTIVE_OS_FINDFILE |TBD| 
|PREEMPTIVE_OS_FLUSHFILEBUFFERS |TBD| 
|PREEMPTIVE_OS_FORMATMESSAGE |TBD| 
|PREEMPTIVE_OS_FREECREDENTIALSHANDLE |TBD| 
|PREEMPTIVE_OS_FREELIBRARY |TBD| 
|PREEMPTIVE_OS_GENERICOPS |TBD| 
|PREEMPTIVE_OS_GETADDRINFO |TBD| 
|PREEMPTIVE_OS_GETCOMPRESSEDFILESIZE |TBD| 
|PREEMPTIVE_OS_GETDISKFREESPACE |TBD| 
|PREEMPTIVE_OS_GETFILEATTRIBUTES |TBD| 
|PREEMPTIVE_OS_GETFILESIZE |TBD| 
|PREEMPTIVE_OS_GETFINALFILEPATHBYHANDLE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_OS_GETLONGPATHNAME |TBD| 
|PREEMPTIVE_OS_GETPROCADDRESS |TBD| 
|PREEMPTIVE_OS_GETVOLUMENAMEFORVOLUMEMOUNTPOINT |TBD| 
|PREEMPTIVE_OS_GETVOLUMEPATHNAME |TBD| 
|PREEMPTIVE_OS_INITIALIZESECURITYCONTEXT |TBD| 
|PREEMPTIVE_OS_LIBRARYOPS |TBD| 
|PREEMPTIVE_OS_LOADLIBRARY |TBD| 
|PREEMPTIVE_OS_LOGONUSER |TBD| 
|PREEMPTIVE_OS_LOOKUPACCOUNTSID |TBD| 
|PREEMPTIVE_OS_MESSAGEQUEUEOPS |TBD| 
|PREEMPTIVE_OS_MOVEFILE |TBD| 
|PREEMPTIVE_OS_NETGROUPGETUSERS |TBD| 
|PREEMPTIVE_OS_NETLOCALGROUPGETMEMBERS |TBD| 
|PREEMPTIVE_OS_NETUSERGETGROUPS |TBD| 
|PREEMPTIVE_OS_NETUSERGETLOCALGROUPS |TBD| 
|PREEMPTIVE_OS_NETUSERMODALSGET |TBD| 
|PREEMPTIVE_OS_NETVALIDATEPASSWORDPOLICY |TBD| 
|PREEMPTIVE_OS_NETVALIDATEPASSWORDPOLICYFREE |TBD| 
|PREEMPTIVE_OS_OPENDIRECTORY |TBD| 
|PREEMPTIVE_OS_PDH_WMI_INIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_OS_PIPEOPS |TBD| 
|PREEMPTIVE_OS_PROCESSOPS |TBD| 
|PREEMPTIVE_OS_QUERYCONTEXTATTRIBUTES |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_OS_QUERYREGISTRY |TBD| 
|PREEMPTIVE_OS_QUERYSECURITYCONTEXTTOKEN |TBD| 
|PREEMPTIVE_OS_REMOVEDIRECTORY |TBD| 
|PREEMPTIVE_OS_REPORTEVENT |TBD| 
|PREEMPTIVE_OS_REVERTTOSELF |TBD| 
|PREEMPTIVE_OS_RSFXDEVICEOPS |TBD| 
|PREEMPTIVE_OS_SECURITYOPS |TBD| 
|PREEMPTIVE_OS_SERVICEOPS |TBD| 
|PREEMPTIVE_OS_SETENDOFFILE |TBD| 
|PREEMPTIVE_OS_SETFILEPOINTER |TBD| 
|PREEMPTIVE_OS_SETFILEVALIDDATA |TBD| 
|PREEMPTIVE_OS_SETNAMEDSECURITYINFO |TBD| 
|PREEMPTIVE_OS_SQLCLROPS |TBD| 
|PREEMPTIVE_OS_SQMLAUNCH |TBD <br /> **Применимо к**: с [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]. |  
|PREEMPTIVE_OS_VERIFYSIGNATURE |TBD| 
|PREEMPTIVE_OS_VERIFYTRUST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_OS_VSSOPS |TBD| 
|PREEMPTIVE_OS_WAITFORSINGLEOBJECT |TBD| 
|PREEMPTIVE_OS_WINSOCKOPS |TBD| 
|PREEMPTIVE_OS_WRITEFILE |TBD| 
|PREEMPTIVE_OS_WRITEFILEGATHER |TBD| 
|PREEMPTIVE_OS_WSASETLASTERROR |TBD| 
|PREEMPTIVE_REENLIST |TBD| 
|PREEMPTIVE_RESIZELOG |TBD| 
|PREEMPTIVE_ROLLFORWARDREDO |TBD| 
|PREEMPTIVE_ROLLFORWARDUNDO |TBD| 
|PREEMPTIVE_SB_STOPENDPOINT |TBD| 
|PREEMPTIVE_SERVER_STARTUP |TBD| 
|PREEMPTIVE_SETRMINFO |TBD| 
|PREEMPTIVE_SHAREDMEM_GETDATA |TBD| 
|PREEMPTIVE_SNIOPEN |TBD| 
|PREEMPTIVE_SOSHOST |TBD| 
|PREEMPTIVE_SOSTESTING |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PREEMPTIVE_SP_SERVER_DIAGNOSTICS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_STARTRM |TBD| 
|PREEMPTIVE_STREAMFCB_CHECKPOINT |TBD| 
|PREEMPTIVE_STREAMFCB_RECOVER |TBD| 
|PREEMPTIVE_STRESSDRIVER |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PREEMPTIVE_TESTING |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PREEMPTIVE_TRANSIMPORT |TBD| 
|PREEMPTIVE_UNMARSHALPROPAGATIONTOKEN |TBD| 
|PREEMPTIVE_VSS_CREATESNAPSHOT |TBD| 
|PREEMPTIVE_VSS_CREATEVOLUMESNAPSHOT |TBD| 
|PREEMPTIVE_XE_CALLBACKEXECUTE |TBD| 
|PREEMPTIVE_XE_CX_FILE_OPEN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_XE_CX_HTTP_CALL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PREEMPTIVE_XE_DISPATCHER |TBD| 
|PREEMPTIVE_XE_ENGINEINIT |TBD| 
|PREEMPTIVE_XE_GETTARGETSTATE |TBD| 
|PREEMPTIVE_XE_SESSIONCOMMIT |TBD| 
|PREEMPTIVE_XE_TARGETFINALIZE |TBD| 
|PREEMPTIVE_XE_TARGETINIT |TBD| 
|PREEMPTIVE_XE_TIMERRUN |TBD| 
|PREEMPTIVE_XETESTING |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|PRINT_ROLLBACK_PROGRESS |Применяется при ожидании завершения пользовательских процессов в базе данных, измененной с помощью заключительного предложения ALTER DATABASE. Дополнительные сведения см. в разделе инструкции ALTER DATABASE (Transact-SQL).| 
|PRU_ROLLBACK_DEFERRED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_ALL_COMPONENTS_INITIALIZED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_COOP_SCAN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_DIRECTLOGCONSUMER_GETNEXT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_EVENT_SESSION_INIT_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_FABRIC_REPLICA_CONTROLLER_DATA_LOSS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_ACTION_COMPLETED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_CHANGE_NOTIFIER_TERMINATION_SYNC |Происходит, когда фоновая задача ожидает завершения фоновой задачей, которая получает (путем опроса) уведомления отказоустойчивой кластеризации Windows Server., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_CLUSTER_INTEGRATION |Добавления, замены или удаления ожидает получения блокировки на Always On внутренний список (например, список сетей, сетевых адресов или прослушивателей группы доступности) запись операции. Только для внутреннего использования <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_FAILOVER_COMPLETED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_JOIN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_OFFLINE_COMPLETED |Always On операция удаления группы доступности находится в состоянии ожидания целевая группа доступности в автономный режим перед удалением объектов отказоустойчивой кластеризации Windows Server., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_ONLINE_COMPLETED |Всегда на создание или операция группы доступности перехода на другой ресурс ожидает целевая группа доступности перешел в оперативный режим., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_POST_ONLINE_COMPLETED |Always On операция удаления группы доступности ожидает завершения любой фоновой задачи, которая была запланирована во время выполнения предыдущей команды. Например, это может быть фоновая задача, которая превращает базы данных доступности в основные базы данных. DROP AVAILABILITY GROUP языка DDL необходимо дождаться этой фоновой задачи во избежание конкуренции., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_SERVER_READY_CONNECTIONS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADR_WORKITEM_COMPLETED |Внутреннее ожидание: поток ожидает завершения асинхронной рабочей задачи. Это ожидание предусмотрено и является используйте CSS., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_HADRSIM |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_LOG_CONSOLIDATION_IO |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_LOG_CONSOLIDATION_POLL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_MD_LOGIN_STATS |Имеет место в процессе внутренней синхронизации метаданных статистики входа в систему., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_MD_RELATION_CACHE |Имеет место в процессе внутренней синхронизации метаданных для таблицы или индекса., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_MD_SERVER_CACHE |Имеет место в процессе внутренней синхронизации метаданных на связанных серверах., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_MD_UPGRADE_CONFIG |Имеет место в процессе внутренней синхронизации при обновлении конфигурации уровня сервера., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_PREEMPTIVE_APP_USAGE_TIMER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_PREEMPTIVE_AUDIT_ACCESS_WINDOWSLOG |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_QRY_BPMEMORY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_REPLICA_ONLINE_INIT_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_RESOURCE_SEMAPHORE_FT_PARALLEL_QUERY_SYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_SBS_FILE_OPERATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_XTP_FSSTORAGE_MAINTENANCE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|PWAIT_XTP_HOST_STORAGE_WAIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_ASYNC_CHECK_CONSISTENCY_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_ASYNC_PERSIST_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_ASYNC_PERSIST_TASK_START |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_ASYNC_QUEUE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_BCKG_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_BLOOM_FILTER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_CLEANUP_STALE_QUERIES_TASK_MAIN_LOOP_SLEEP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_CTXS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_DB_DISK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_DYN_VECTOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_EXCLUSIVE_ACCESS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_HOST_INIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_LOADDB |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_PERSIST_TASK_MAIN_LOOP_SLEEP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_QDS_CAPTURE_INIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_SHUTDOWN_QUEUE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_STMT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_STMT_DISK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_TASK_SHUTDOWN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QDS_TASK_START |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QE_WARN_LIST_SYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QPJOB_KILL |Указывает, что асинхронное автоматическое обновление статистики было отменено с помощью вызова команды KILL во время запуска на выполнение. Завершающий поток приостанавливается и начинает прослушивание команд KILL для своего запуска. Нормальное значение составляет менее 1 секунды.| 
|QPJOB_WAITFOR_ABORT |Указывает, что асинхронное автоматическое обновление статистики было отменено с помощью вызова команды KILL во время выполнения. Обновление в данный момент завершено, но приостановлено до выполнения координации сообщений завершающих потоков. Это обычное, но редкое состояние, которое должно длиться очень короткое время. Нормальное значение составляет менее 1 секунды.| 
|QRY_MEM_GRANT_INFO_MUTEX |Имеет место, когда средство управления памятью при выполнении запросов пытается управлять доступом к статичному списку предоставлений памяти. В этом списке содержатся сведения о текущей предоставленной памяти и ожидающих запросах на ее выделение. Данное состояние является стандартным при управлении доступом. Его ожидание не должно длиться долго. Если мьютекс не будет освобожден, все новые запросы, использующие память, перестанут отвечать.| 
|QRY_PARALLEL_THREAD_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QRY_PROFILE_LIST_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QUERY_ERRHDL_SERVICE_DONE |Указано только в ознакомительных целях. Не поддерживается. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|QUERY_WAIT_ERRHDL_SERVICE |Указано только в ознакомительных целях.  Не поддерживается. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только.  |  
|QUERY_EXECUTION_INDEX_SORT_EVENT_OPEN |Имеет место в определенных случаях, когда параллельно выполняется создание индекса вне сети, а различные выполняющие сортировку исполнители синхронизируют доступ к файлам сортировки.| 
|QUERY_NOTIFICATION_MGR_MUTEX |Имеет место в процессе синхронизации очереди сборки мусора в диспетчере уведомлений о запросах.| 
|QUERY_NOTIFICATION_SUBSCRIPTION_MUTEX |Имеет место в процессе синхронизации состояния транзакций в уведомлениях о запросах.| 
|QUERY_NOTIFICATION_TABLE_MGR_MUTEX |Имеет место в процессе внутренней синхронизации диспетчера уведомлений о запросах.| 
|QUERY_NOTIFICATION_UNITTEST_MUTEX |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|QUERY_OPTIMIZER_PRINT_MUTEX |Имеет место в процессе синхронизации диагностического выхода оптимизатора запросов. Этот тип ожидания возникает только в том случае, если были включены настройки диагностики под руководством службы поддержки продуктов Майкрософт.| 
|QUERY_TASK_ENQUEUE_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|QUERY_TRACEOUT |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|RBIO_WAIT_VLF |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|RECOVER_CHANGEDB |Имеет место в процессе синхронизации состояния базы данных в режиме «горячего» резервирования.| 
|RECOVERY_MGR_LOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REDO_THREAD_PENDING_WORK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REDO_THREAD_SYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REMOTE_BLOCK_IO |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REMOTE_DATA_ARCHIVE_MIGRATION_DMV |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REMOTE_DATA_ARCHIVE_SCHEMA_DMV |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REMOTE_DATA_ARCHIVE_SCHEMA_TASK_QUEUE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REPL_CACHE_ACCESS |Имеет место в процессе синхронизации кэша статей репликации. В процессе таких ожиданий средство чтения журнала репликаций простаивает, а DDL-инструкции к опубликованной таблице блокируются.| 
|REPL_HISTORYCACHE_ACCESS |TBD| 
|REPL_SCHEMA_ACCESS |Имеет место в процессе синхронизации данных о версии схемы репликации. Это состояние имеет место в случаях, когда DDL-инструкции выполняются над реплицируемым объектом, а средство чтения журнала создает или использует схему с управлением версиями на основе вхождения DDL. Состязание может отображаться на этот тип ожидания, если имеется много опубликованных баз данных на один издатель при репликации транзакций и опубликованных баз данных очень активны.| 
|REPL_TRANFSINFO_ACCESS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REPL_TRANHASHTABLE_ACCESS |TBD| 
|REPL_TRANTEXTINFO_ACCESS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|REPLICA_WRITES |Имеет место при ожидании задачей завершения записи страниц в моментальные снимки базы данных или реплики DBCC.| 
|REQUEST_DISPENSER_PAUSE |Имеет место при ожидании задачей завершения всех текущих операций ввода-вывода, чтобы ввод-вывод в файл можно было приостановить для выполнения резервного копирования моментального снимка.| 
|REQUEST_FOR_DEADLOCK_SEARCH |Имеет место в случае, когда монитор взаимоблокировок ожидает запуска следующего поиска взаимоблокировки. Это ожидаемое состояние между выявлениями взаимоблокировок, и длительное общее время ожидания этого ресурса не указывает на проблему.| 
|RESERVED_MEMORY_ALLOCATION_EXT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|RESMGR_THROTTLED |Имеет место, когда новый запрос поступает и повторяется в соответствии со значением параметра GROUP_MAX_REQUESTS.| 
|RESOURCE_GOVERNOR_IDLE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|RESOURCE_QUEUE |Имеет место в процессе синхронизации различных внутренних очередей ресурсов.| 
|RESOURCE_SEMAPHORE |Имеет место в случае, когда запрос памяти из очереди не может быть выполнен немедленно из-за других параллельных запросов. Высокие значения ожиданий и времени ожидания могут указывать на чрезмерное количество параллельных запросов или чрезмерные объемы запрашиваемой памяти.| 
|RESOURCE_SEMAPHORE_MUTEX |Имеет место в случае, когда запрос ожидает выполнения запроса на резервирование потока. Также имеет место при запросах на компиляцию и выделение памяти в процессе синхронизации.| 
|RESOURCE_SEMAPHORE_QUERY_COMPILE |Имеет место в случае, когда количество параллельных компиляций запросов достигает предела повтора. Высокие значения ожиданий и времени ожидания могут указывать на чрезмерное количество компиляций, повторных компиляций или некэшируемых планов.| 
|RESOURCE_SEMAPHORE_SMALL_QUERY |Имеет место в случае, когда небольшой запрос не может быть выполнен немедленно из-за других параллельных запросов. Время ожидания не должно превышать нескольких секунд, так как при невозможности выделения запрошенной памяти в течение нескольких секунд сервер передает запрос в главный пул памяти для запросов. Высокие значения ожиданий могут указывать на чрезмерное количество параллельных небольших запросов, в то время как главный пул памяти заблокирован ожидающими запросами. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|RESTORE_FILEHANDLECACHE_ENTRYLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|RESTORE_FILEHANDLECACHE_LOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|RG_RECONFIG |TBD| 
|ROWGROUP_OP_STATS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|ROWGROUP_VERSION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|RTDATA_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SATELLITE_CARGO |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SATELLITE_SERVICE_SETUP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SATELLITE_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SBS_DISPATCH |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SBS_RECEIVE_TRANSPORT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SBS_TRANSPORT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SCAN_CHAR_HASH_ARRAY_INITIALIZATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SEC_DROP_TEMP_KEY |Имеет место после неудачной попытки удаления временного ключа безопасности перед повторной попыткой.| 
|SECURITY_CNG_PROVIDER_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SECURITY_CRYPTO_CONTEXT_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SECURITY_DBE_STATE_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SECURITY_KEYRING_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SECURITY_MUTEX |Имеет место при ожидании мьютексов, контролирующих доступ к глобальному списку поставщиков служб шифрования расширенного управления ключами и списку сеансов расширенного управления ключами, ограниченному областью сеанса.| 
|SECURITY_RULETABLE_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SEMPLAT_DSI_BUILD |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SEQUENCE_GENERATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SEQUENTIAL_GUID |Имеет место при получении нового последовательного значения идентификатора GUID.| 
|SERVER_IDLE_CHECK |Происходит во время синхронизации состояния простоя экземпляра SQL Server, когда монитор ресурсов пытается объявить экземпляр SQL Server как простоя или пытающимся пробудиться.| 
|SERVER_RECONFIGURE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SESSION_WAIT_STATS_CHILDREN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SHARED_DELTASTORE_CREATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SHUTDOWN |Имеет место, когда инструкция завершения работы ожидает закрытия активных соединений.| 
|SLEEP_BPOOL_FLUSH |Имеет место при повторе контрольной точкой выпуска новых операций ввода-вывода во избежание переполнения дисковой подсистемы.| 
|SLEEP_BUFFERPOOL_HELPLW |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLEEP_DBSTARTUP |Имеет место в процессе запуска базы данных при ожидании восстановления всех баз данных.| 
|SLEEP_DCOMSTARTUP |Происходит один раз, в большинстве случаев во время запуска экземпляра SQL Server при ожидании завершения инициализации DCOM.| 
|SLEEP_MASTERDBREADY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLEEP_MASTERMDREADY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLEEP_MASTERUPGRADED |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLEEP_MEMORYPOOL_ALLOCATEPAGES |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLEEP_MSDBSTARTUP |Имеет место при ожидании трассировки SQL запуска базы данных msdb.| 
|SLEEP_RETRY_VIRTUALALLOC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLEEP_SYSTEMTASK |Имеет место при запуске фоновой задачи во время ожидания запуска базы данных tempdb.| 
|SLEEP_TASK |Имеет место в случае, когда задача находится в неактивном состоянии во время ожидания универсального события.| 
|SLEEP_TEMPDBSTARTUP |Имеет место при ожидании задачей запуска базы данных tempdb.| 
|SLEEP_WORKSPACE_ALLOCATEPAGE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SLO_UPDATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SMSYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SNI_CONN_DUP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SNI_CRITICAL_SECTION |Происходит во время внутренней синхронизации в сетевых компонентов SQL Server.| 
|SNI_HTTP_WAITFOR_0_DISCON |Происходит при завершении работы SQL Server, во время ожидания для выхода из имеющихся HTTP-соединений.| 
|SNI_LISTENER_ACCESS |Имеет место при ожидании обновления изменения состояния узлов доступа к неоднородной памяти (NUMA). Доступ к изменению состояния сериализован.| 
|SNI_TASK_COMPLETION |Имеет место при ожидании завершения всех задач во время изменения состояния узла NUMA.| 
|SNI_WRITE_ASYNC |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SOAP_READ |Имеет место при ожидании завершения операции чтения HTTP-данных из сети.| 
|SOAP_WRITE |Имеет место при ожидании завершения операции записи HTTP-данных по сети.| 
|SOCKETDUPLICATEQUEUE_CLEANUP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SOS_CALLBACK_REMOVAL |Имеет место при выполнении синхронизации списка обратных вызовов с целью удаления обратного вызова. Изменение этого счетчика после выполнения инициализации сервера не ожидается.| 
|SOS_DISPATCHER_MUTEX |Имеет место при выполнении внутренней синхронизации пула диспетчеров. Это также относится и к настройке пула.| 
|SOS_LOCALALLOCATORLIST |Имеет место в процессе внутренней синхронизации в диспетчере памяти [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|SOS_MEMORY_TOPLEVELBLOCKALLOCATOR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SOS_MEMORY_USAGE_ADJUSTMENT |Имеет место при распределении памяти между пулами.| 
|SOS_OBJECT_STORE_DESTROY_MUTEX |Имеет место в процессе внутренней синхронизации в пулах памяти во время удаления объектов из пула.| 
|SOS_PHYS_PAGE_CACHE |Определяет время ожидания потока для получения объекта взаимного исключения, который он должен получить перед выделением физических страниц или перед возвращением этих страниц операционной системе. Ожидания данного типа появляются, только если экземпляр SQL Server использует память AWE., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SOS_PROCESS_AFFINITY_MUTEX |Имеет место в процессе синхронизации доступа для обработки настроек схожести.| 
|SOS_RESERVEDMEMBLOCKLIST |Происходит во время внутренней синхронизации в диспетчере памяти SQL Server. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|SOS_SCHEDULER_YIELD |Имеет место, когда задача добровольно отказывается от выполнения планировщиком в пользу других задач. В течение этого ожидания задача ожидает обновления своего такта.| 
|SOS_SMALL_PAGE_ALLOC |Имеет место при выделении и освобождении памяти, управляемой некоторыми объектами памяти.| 
|SOS_STACKSTORE_INIT_MUTEX |Имеет место в процессе синхронизации внутренней инициализации хранилища.| 
|SOS_SYNC_TASK_ENQUEUE_EVENT |Имеет место при запуске задачи в синхронном режиме. Большинство задач в SQL Server запускаются в асинхронном режиме, при котором управление возвращается процессу, запустившему сразу после запроса на задачу было помещено в очередь.| 
|SOS_VIRTUALMEMORY_LOW |Имеет место при выделении памяти в случае ожидания освобождения виртуальной памяти менеджером ресурсов.| 
|SOSHOST_EVENT |Происходит, когда включенный компонент, например среда CLR, ожидает объекта синхронизации событий SQL Server.| 
|SOSHOST_INTERNAL |Имеет место в процессе синхронизации обратных вызовов диспетчера памяти, используемых включенными компонентами, например средой CLR.| 
|SOSHOST_MUTEX |Происходит, когда включенный компонент, например среда CLR, ожидает объекта синхронизации мьютекс SQL Server.| 
|SOSHOST_RWLOCK |Происходит, когда включенный компонент, например среда CLR, ожидает объекта синхронизации чтения записи SQL Server.| 
|SOSHOST_SEMAPHORE |Происходит, когда включенный компонент, например среда CLR, ожидает объекта синхронизации семафоров SQL Server.| 
|SOSHOST_SLEEP |Имеет место в случае, когда включенная задача находится в неактивном состоянии во время ожидания универсального события. Включенные задачи используются включенными компонентами, например средой CLR.| 
|SOSHOST_TRACELOCK |Имеет место в процессе синхронизации доступа к потокам трассировки.| 
|SOSHOST_WAITFORDONE |Имеет место в случае, когда включенный компонент, например среда CLR, ожидает завершения выполнения задачи.| 
|SP_PREEMPTIVE_SERVER_DIAGNOSTICS_SLEEP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SP_SERVER_DIAGNOSTICS_BUFFER_ACCESS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SP_SERVER_DIAGNOSTICS_INIT_MUTEX |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SP_SERVER_DIAGNOSTICS_SLEEP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SQLCLR_APPDOMAIN |Имеет место в случае, когда среда CLR ожидает завершения запуска домена приложений.| 
|SQLCLR_ASSEMBLY |Имеет место при ожидании доступа к списку загруженных сборок в домене приложений.| 
|SQLCLR_DEADLOCK_DETECTION |Имеет место в случае, когда среда CLR ожидает завершения выявления взаимоблокировок.| 
|SQLCLR_QUANTUM_PUNISHMENT |Имеет место в случае повтора задачи CLR из-за превышения такта на выполнение. Повтор производится с целью снижения влияния задачи, интенсивно использующей ресурсы, на другие задачи.| 
|SQLSORT_NORMMUTEX |Имеет место в процессе внутренней синхронизации во время инициализации внутренних структур сортировки.| 
|SQLSORT_SORTMUTEX |Имеет место в процессе внутренней синхронизации во время инициализации внутренних структур сортировки.| 
|SQLTRACE_BUFFER_FLUSH |Имеет место, когда задача ожидает сохранения фоновой задачей буферов трассировки на диск каждые четыре секунды. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|SQLTRACE_FILE_BUFFER |Имеет место в процессе синхронизации буферов трассировки во время трассировки файлов., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SQLTRACE_FILE_READ_IO_COMPLETION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SQLTRACE_FILE_WRITE_IO_COMPLETION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SQLTRACE_INCREMENTAL_FLUSH_SLEEP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SQLTRACE_LOCK |TBD <br /> **Область применения**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|SQLTRACE_PENDING_BUFFER_WRITERS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|SQLTRACE_SHUTDOWN |Имеет место в случае, когда операция завершения трассировки ожидает завершения имеющихся событий трассировки.| 
|SQLTRACE_WAIT_ENTRIES |Имеет место, когда очередь событий трассировки SQL ожидает поступления пакетов в очередь.| 
|SRVPROC_SHUTDOWN |Имеет место в случае, когда процесс завершения работы ожидает освобождения внутренних ресурсов для верного завершения работы.| 
|STARTUP_DEPENDENCY_MANAGER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|TDS_BANDWIDTH_STATE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|TDS_INIT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|TDS_PROXY_CONTAINER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|TEMPOBJ |Имеет место при синхронизации удалений временных объектов. Этот тип ожидания является редким и имеет место только в случае, если задача запросила монопольный доступ на удаление таблиц temp.| 
|TEMPORAL_BACKGROUND_PROCEED_CLEANUP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|TERMINATE_LISTENER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|THREADPOOL |Имеет место, когда задача ожидает запуска исполнителем. Это ожидание может указывать на недостаточное число исполнителей или на то, что выполнение пакетов занимает слишком много времени, поэтому число доступных исполнителей уменьшилось из-за необходимости обработки других пакетов.| 
|TIMEPRIV_TIMEPERIOD |Имеет место при выполнении внутренней синхронизации таймера расширенных событий.| 
|TRACE_EVTNOTIF |TBD| 
|TRACEWRITE |Имеет место, когда поставщик трассировки наборов строк трассировки SQL ожидает либо свободного буфера, либо буфера с событиями для обработки.| 
|TRAN_MARKLATCH_DT |Имеет место при ожидании кратковременной блокировки режима удаления для кратковременной блокировки метки транзакции. Кратковременные блокировки меток транзакций используются для синхронизации фиксаций с помеченными транзакциями.| 
|TRAN_MARKLATCH_EX |Имеет место при ожидании кратковременной блокировки монопольного режима для помеченной транзакции. Кратковременные блокировки меток транзакций используются для синхронизации фиксаций с помеченными транзакциями.| 
|TRAN_MARKLATCH_KP |Имеет место при ожидании кратковременной блокировки режима удержания для помеченной транзакции. Кратковременные блокировки меток транзакций используются для синхронизации фиксаций с помеченными транзакциями.| 
|TRAN_MARKLATCH_NL |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|TRAN_MARKLATCH_SH |Имеет место при ожидании кратковременной блокировки общего режима для помеченной транзакции. Кратковременные блокировки меток транзакций используются для синхронизации фиксаций с помеченными транзакциями.| 
|TRAN_MARKLATCH_UP |Имеет место при ожидании кратковременной блокировки режима обновления для помеченной транзакции. Кратковременные блокировки меток транзакций используются для синхронизации фиксаций с помеченными транзакциями.| 
|TRANSACTION_MUTEX |Имеет место в процессе синхронизации доступа к транзакции из нескольких пакетов.| 
|UCS_ENDPOINT_CHANGE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|UCS_MANAGER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|UCS_MEMORY_NOTIFICATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|UCS_SESSION_REGISTRATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|UCS_TRANSPORT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|UCS_TRANSPORT_STREAM_CHANGE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|UTIL_PAGE_ALLOC |Имеет место в случае, когда операции просмотра журналов транзакций ожидают освобождения памяти в условиях чрезмерной загрузки.| 
|VDI_CLIENT_COMPLETECOMMAND |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|VDI_CLIENT_GETCOMMAND |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|VDI_CLIENT_OPERATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|VDI_CLIENT_OTHER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|VERSIONING_COMMITTING |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|VIA_ACCEPT |Имеет место при завершении соединения с поставщиком VIA во время запуска.| 
|VIEW_DEFINITION_MUTEX |Имеет место в процессе синхронизации доступа к кэшированным определениям представлений.| 
|WAIT_FOR_RESULTS |Имеет место при ожидании срабатывания триггера уведомления запроса.| 
|WAIT_SCRIPTDEPLOYMENT_REQUEST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_SCRIPTDEPLOYMENT_WORKER |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XLOGREAD_SIGNAL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_ASYNC_TX_COMPLETION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_CKPT_AGENT_WAKEUP |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_CKPT_CLOSE |Имеет место при ожидании завершения контрольной точки., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_CKPT_ENABLED |Происходит, когда назначение контрольных точек отключена и система ожидает создания контрольных точек должно быть включено., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_CKPT_STATE_LOCK |Возникает при синхронизации проверки состояния контрольной точки., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_COMPILE_WAIT |TBD <br /> **ПРИМЕНИМО К**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_GUEST |Происходит, когда нужно прекратить получение уведомлений о нехватке памяти выделения памяти базы данных., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_HOST_WAIT |Происходит, когда ожиданий активируемой компонентом database engine и реализовано узлом., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_OFFLINE_CKPT_BEFORE_REDO |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_OFFLINE_CKPT_LOG_IO |Происходит, когда автономная контрольная точка ожидает завершения операции чтения журнала., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_OFFLINE_CKPT_NEW_LOG |Происходит, когда автономная контрольная точка ожидает новых записей журнала для проверки., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_PROCEDURE_ENTRY |Происходит, когда процедура удаления ожидает завершения всех текущих выполнений этой процедуры для выполнения., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_RECOVERY |Возникает при ожидании восстановления оптимизированных для памяти объектов, чтобы завершить восстановление базы данных., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_SERIAL_RECOVERY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_SWITCH_TO_INACTIVE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_TASK_SHUTDOWN |Имеет место при ожидании завершения потока OLTP в памяти., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAIT_XTP_TRAN_DEPENDENCY |Имеет место при ожидании зависимостей транзакции., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAITFOR |Возникает в результате инструкцию WAITFOR Transact-SQL. Длительность ожидания определяется параметрами инструкции. Это ожидание инициируется пользователем.| 
|WAITFOR_PER_QUEUE |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WAITFOR_TASKSHUTDOWN |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|WAITSTAT_MUTEX |Имеет место в процессе синхронизации доступа к коллекции статистик, используемой для заполнения представления sys.dm_os_wait_stats.| 
|WCC |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|WINDOW_AGGREGATES_MULTIPASS |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WINFAB_API_CALL |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WINFAB_REPLICA_BUILD_OPERATION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WINFAB_REPORT_FAULT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|WORKTBL_DROP |Имеет место в случае приостановки перед повторной попыткой, после неудачной попытки удаления рабочей таблицы.| 
|WRITE_COMPLETION |Имеет место при выполнении операции записи.| 
|WRITELOG |Имеет место при ожидании завершения записи журнала. Обычно запись журнала вызывается такими операциями, как контрольные точки и фиксации транзакций.| 
|XACT_OWN_TRANSACTION |Имеет место при ожидании получения прав на владение транзакцией.| 
|XACT_RECLAIM_SESSION |Имеет место при ожидании отказа текущего владельца сеанса от владения им.| 
|XACTLOCKINFO |Имеет место в процессе синхронизации доступа к списку блокировок для транзакции. В дополнение к самой транзакции к списку имеют доступ такие операции, как выявление взаимоблокировок и миграция блокировок во время разбиения страниц.| 
|XACTWORKSPACE_MUTEX |Имеет место в процессе синхронизации исключений из транзакции, а также синхронизации числа блокировок базы данных между прикрепленными участниками транзакции.| 
|XDB_CONN_DUP_HASH |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XDES_HISTORY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XDES_OUT_OF_ORDER_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XDES_SNAPSHOT |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XDESTSVERMGR |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XE_BUFFERMGR_ALLPROCESSED_EVENT |Происходит, если буферы сеанса расширенных событий записываются в целевые объекты. Это происходит в фоновом потоке.| 
|XE_BUFFERMGR_FREEBUF_EVENT |Происходит, если верно любое из следующих условий.| 
|XE_CALLBACK_LIST |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XE_CX_FILE_READ |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XE_DISPATCHER_CONFIG_SESSION_LIST |Происходит при запуске или остановке сеанса расширенных событий, в котором используются асинхронные целевые объекты. Этот случай ожидания указывает на то, что имеет место одно из следующих условий.| 
|XE_DISPATCHER_JOIN |Происходит при завершении фонового потока, который используется для сеансов расширенных событий.| 
|XE_DISPATCHER_WAIT |Происходит, если фоновый поток, который используется для сеансов расширенных событий, ожидает обработки буферов событий.| 
|XE_FILE_TARGET_TVF |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XE_LIVE_TARGET_TVF |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XE_MODULEMGR_SYNC |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|XE_OLS_LOCK |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.| 
|XE_PACKAGE_LOCK_BACKOFF |Указано только в ознакомительных целях. Не поддерживается. <br /> **Применяется к**: [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] только. |  
|XE_SERVICES_EVENTMANUAL |TBD| 
|XE_SERVICES_MUTEX |TBD| 
|XE_SERVICES_RWLOCK |TBD| 
|XE_SESSION_CREATE_SYNC |TBD| 
|XE_SESSION_FLUSH |TBD| 
|XE_SESSION_SYNC |TBD| 
|XE_STM_CREATE |TBD| 
|XE_TIMER_EVENT |TBD| 
|XE_TIMER_MUTEX |TBD| 
|XE_TIMER_TASK_DONE |TBD| 
|XIO_CREDENTIAL_MGR_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XIO_CREDENTIAL_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XIO_EDS_MGR_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XIO_EDS_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XIO_IOSTATS_BLOBLIST_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XIO_IOSTATS_FCBLIST_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XIO_LEASE_RENEW_MGR_RWLOCK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTP_HOST_DB_COLLECTION |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTP_HOST_LOG_ACTIVITY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTP_HOST_PARALLEL_RECOVERY |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTP_PREEMPTIVE_TASK |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTP_TRUNCATION_LSN |TBD <br /> **Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTPPROC_CACHE_ACCESS |Возникает при ожидании доступа ко все объекты кэша скомпилированной хранимой процедуры., <br /> **Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
|XTPPROC_PARTITIONED_STACK_CREATE |Происходит при выделении узлов NUMA в собственном коде компиляции хранимой процедуры кэша структуры (происходит в одном потоке) для данной процедуры., <br /> **Применимо к**: с [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|

  
 Следующие события XEvents относятся к секции **КОММУТАТОРА** и перестроению индекса в сети. Сведения о синтаксисе см. в разделе [ALTER TABLE &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md) и [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
-   lock_request_priority_state  
  
-   process_killed_by_abort_blockers  
  
-   ddl_with_wait_at_low_priority  
  
 Матрицу совместимости блокировок см. в разделе [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md).  
  
## <a name="see-also"></a>См. также  
    
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_session_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md)   
 [sys.dm_db_wait_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-wait-stats-azure-sql-database.md)  
  
  


