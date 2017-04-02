---
title: "Автоматическая инициализация группы доступности Always On | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67c6a601-677a-402b-b3d1-8c65494e9e96
caps.latest.revision: 18
ms.author: "v-saume"
manager: "jhubbard"
---
# Автоматическая инициализация группы доступности Always On
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


 В SQL Server 2016 добавлена функция автоматического заполнения групп доступности. При создании группы доступности с автоматическим заполнением SQL Server автоматически создает вторичные реплики для каждой базы данных в группе. Благодаря автоматическому заполнению больше не требуется вручную выполнять операции резервного копирования и восстановления вторичных реплик. Чтобы включить автоматическое заполнение, нужно создать группу доступности с помощью T-SQL.
 
## Предварительные требования

Для работы автоматического заполнения путь к файлу данных и файлу журнала должен быть одинаковым на каждом экземпляре SQL Server, входящем в группу доступности. 

Заполнение группы доступности осуществляется через конечную точку зеркального отображения базы данных. Откройте правила брандмауэра для входящего трафика на порту конечной точки зеркального отображения на каждом сервере.

Базы данных в группе доступности должны использовать модель полного восстановления. База данных должна иметь актуальную полную резервную копию и резервную копию журнала транзакций. Эти файлы резервных копий не используются для автоматического заполнения, но они необходимы до включения базы данных в группу доступности. 
 
## Создание группы доступности с помощью автоматического заполнения

Чтобы создать группу доступности с помощью автоматического заполнения, задайте `SEEDING_MODE=AUTOMATIC`. 

В следующем примере показано создание группы доступности в двухузловом отказоустойчивом кластере Windows Server. Перед запуском сценариев обновите значения для имеющейся среды.

1. Создайте конечные точки. Конечная точка потребуется для каждого сервера. В следующем скрипте создается конечная точка, которая использует TCP-порт 5022 для прослушивателя. Задайте `<endpoint_name>` и `LISTENER_PORT` в соответствии со средой и выполните сценарий:

    ```
    --Create the endpoint on both servers
    -- Run this script twice, once on each server. 
    CREATE ENDPOINT [<endpoint_name>] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
    FOR DATA_MIRRORING (ROLE = ALL, AUTHENTICATION = WINDOWS NEGOTIATE, ENCRYPTION = REQUIRED ALGORITHM AES)
    GO
    ```

1. Создайте группу доступности. В следующем скрипте создается группа доступности. Обновите значения для имени группы, имен серверов и имен доменов и запустите сценарий на первичном экземпляре SQL Server.  

    ```
    ---Run On Primary
    CREATE AVAILABILITY GROUP [<availability_group_name>]
    FOR DATABASE db1
    REPLICA ON'<*primary_server*>'
    WITH (ENDPOINT_URL = N'TCP://<primary_server>.<fully_qualified_domain_name>:5022', 
    FAILOVER_MODE = AUTOMATIC, 
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
    BACKUP_PRIORITY = 50, 
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO), 
    SEEDING_MODE = AUTOMATIC),
    N'<secondary_server>' WITH (ENDPOINT_URL = N'TCP://<secondary_server>.<fully_qualified_domain_name>:5022', 
    FAILOVER_MODE = AUTOMATIC, 
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
    BACKUP_PRIORITY = 50, 
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO), 
    SEEDING_MODE = AUTOMATIC);
    GO
    ``` 

1. Присоедините сервер-получатель к группе доступности и предоставьте группе разрешение на создание баз данных. Выполните следующий скрипт на вторичном экземпляре SQL Server: 
 
    ```
    --Run on Secondary Replica to join to the availability group
    ALTER AVAILABILITY GROUP [<availability_group_name>] JOIN
    GO  
    ALTER AVAILABILITY GROUP [<availability_group_name>] GRANT CREATE ANY DATABASE
    GO
    ```

SQL Server автоматически создаст реплику базы данных на сервере-получателе. Если размер базы данных слишком велик, завершение синхронизации базы данных займет некоторое время. Если база данных находится в группе доступности, настроенной для автоматического заполнения, можно отправить запрос к системному представлению `sys.dm_hadr_automatic_seeding` на отслеживание хода заполнения. Следующий запрос возвращает одну строку для каждой базы данных в группе доступности, настроенной для автоматического заполнения.

```
 SELECT start_time,
       ag.name,
       db.database_name,
       current_state,
       performed_seeding,
       failure_state,
       failure_state_desc
 FROM sys.dm_hadr_automatic_seeding autos 
    JOIN sys.availability_databases_cluster db ON autos.ag_db_id = db.group_database_id
    JOIN sys.availability_groups ag ON autos.ag_id = ag.group_id
```

## Запрет автоматического заполнения в группе доступности

Чтобы временно запретить первичной реплике заполнение дополнительных баз данных на вторичной реплике, у группы доступности можно отменить разрешение на создание баз данных. Выполните следующий запрос на экземпляре, где размещена вторичная реплика, чтобы запретить группе доступности создавать реплики базы данных.

```
ALTER AVAILABILITY GROUP [<availability_group_name>] DENY CREATE ANY DATABASE
GO
```


## Включение автоматического заполнения в существующей группе доступности

Можно задать автоматическое заполнение в существующей базе данных. Следующая команда изменит группу доступности так, чтобы она использовала автоматическое заполнение. 

```
ALTER AVAILABILITY GROUP [<availability_group_name>] 
MODIFY REPLICA ON '<primary_node>' WITH (SEEDING_MODE = AUTOMATIC)
GO
```

В результате база данных принудительно перезапустит заполнение, если это необходимо. Например, если заполнение завершается сбоем из-за нехватки дискового пространства на вторичной реплике, можно запустить `ALTER AVAILABILITY GROUP ... WITH (SEEDING_MODE=AUTOMATIC)` для перезапуска заполнения после добавления свободного места.

## Остановка автоматического заполнения

Чтобы остановить автоматическое заполнение для группы доступности, запустите следующий сценарий на экземпляре, где размещена первичная реплика:

```
ALTER AVAILABILITY GROUP [<availability_group_name>] 
    MODIFY REPLICA ON '<primary_node>'   
    WITH (SEEDING_MODE = MANUAL)
GO
```

Будут отменены все реплики, находящиеся в режиме заполнения, а SQL Server не сможет автоматически инициализировать реплики в этой группе доступности. При этом синхронизация всех реплик, которые уже инициализированы, остановлена не будет. 


## Мониторинг автоматического заполнения группы доступности

### Использование системных административных представлений для мониторинга заполнения

Следующие системные представления отображают состояние автоматического заполнения SQL Server.

**sys.dm_hadr_automatic_seeding** 

На первичной реплике выполните запрос к `sys.dm_hadr_automatic_seeding` для проверки состояния процесса автоматического заполнения. Представление возвращает одну строку для каждого процесса заполнения. Например:

``` 
SELECT start_time, 
        completion_time
        is_source,
        current_state,
        failure_state,
        failure_state_desc
FROM sys.dm_hadr_automatic_seeding
```
 
**sys.dm_hadr_physical_seeding_stats** 

На первичной реплике выполните запрос к `sys.dm_hadr_physical_seeding_stats` DMV для просмотра физической статистики по каждому процессу заполнения, выполняющемуся в данный момент. Следующий запрос возвращает строки во время выполнения заполнения:

```
SELECT * FROM sys.dm_hadr_physical_seeding_stats;
```

### Диагностика инициализации базы данных с помощью автоматического заполнения в журнале ошибок

При добавлении базы данных в группу доступности, настроенную для автоматического заполнения, SQL Server выполняет резервное копирование VDI в конечной точке группы доступности. Просмотрите журнал ошибок SQL Server на наличие сведений о завершении резервного копирования и синхронизации.

### Диагностика работоспособности уровня базы данных с помощью расширенных событий

Автоматическое заполнение поддерживает новые расширенные события для отслеживания изменения состояния, сбоев и статистики производительности во время инициализации. 

Например, этот скрипт создает сеанс расширенных событий, который фиксирует события, связанные с автоматическим заполнением: 

```
CREATE EVENT SESSION [AlwaysOn_autoseed] ON SERVER 
    ADD EVENT sqlserver.hadr_automatic_seeding_state_transition,
    ADD EVENT sqlserver.hadr_automatic_seeding_timeout,
    ADD EVENT sqlserver.hadr_db_manager_seeding_request_msg,
    ADD EVENT sqlserver.hadr_physical_seeding_backup_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_failure,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_target_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_progress,
    ADD EVENT sqlserver.hadr_physical_seeding_restore_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_submit_callback
    ADD TARGET package0.event_file(SET filename=N’autoseed.xel’,max_file_size=(5),max_rollover_files=(4))
WITH (MAX_MEMORY=4096 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=30 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=ON)
GO 

ALTER EVENT SESSION AlwaysOn_autoseed ON SERVER STATE=START
GO 
```


В таблице ниже перечислены расширенные события, связанные с автоматическим заполнением. 

| Название | Описание|
|------------ |---------------| 
|hadr_db_manager_seeding_request_msg |  Заполнение сообщения запроса.
|hadr_physical_seeding_backup_state_change |    Изменение состояния на стороне резервного копирования при физическом заполнении.
|hadr_physical_seeding_restore_state_change |Изменение состояния на стороне восстановления при физическом заполнении.
|hadr_physical_seeding_forwarder_state_change | Изменение состояния на стороне сервера пересылки при физическом заполнении.
|hadr_physical_seeding_forwarder_target_state_change |  Изменение состояния на стороне цели сервера пересылки при физическом заполнении.
|hadr_physical_seeding_submit_callback  |Событие обратного вызова при фиксации физического заполнения.
|hadr_physical_seeding_failure  |Событие сбоя физического заполнения.
|hadr_physical_seeding_progress |   Событие хода выполнения физического заполнения.
|hadr_physical_seeding_schedule_long_task_failure   |Событие сбоя длительной задачи с расписанием физического заполнения.
|hadr_automatic_seeding_start   |Происходит при отправке операции автоматического заполнения.
|hadr_automatic_seeding_state_transition    |Происходит при изменении состояния операции автоматического заполнения.
|hadr_automatic_seeding_success |Происходит при успешном выполнении операции автоматического заполнения.
|hadr_automatic_seeding_failure |Происходит при сбое операции автоматического заполнения.
|hadr_automatic_seeding_timeout |Происходит при истечении времени ожидания операции автоматического заполнения.

### Другие замечания по устранению неполадок

**Отслеживание завершения автоматического заполнения**

Выполните запрос `sys.dm_hadr_physical_seeding_stats` о текущих выполняющихся процессах автоматического заполнения. Представление возвращает одну строку для каждой базы данных. Например:

```
SELECT local_database_name, 
       role_desc, 
       internal_state_desc, 
       transfer_rate_bytes_per_second, 
       transferred_size_bytes, 
       database_size_bytes, 
       start_time_utc, 
       end_time_utc, estimate_time_complete_utc, 
       total_disk_io_wait_time_ms, 
       total_network_wait_time_ms, 
       is_compression_enabled 
FROM sys.dm_hadr_physical_seeding_stats
```

**Устранение неполадок, связанных с ошибкой отображения базы данных в группе доступности, настроенной для автоматического заполнения**


Если база данных не отображается в составе группы доступности с включенным автоматическим заполнением, скорее всего, произошел сбой автоматического заполнения. Это делает невозможным добавление базы данных в группу доступности на первичной или вторичной репликах. Выполните запрос `sys.dm_hadr_automatic_seeding` на первичной и вторичной репликах. Например, выполните следующий запрос, чтобы определить состояние сбоя автоматического заполнения.

```
SELECT start_time, 
       completion_time, 
       is_source, 
       current_state, 
       failure_state, 
       failure_state_desc, 
       error_code 
FROM sys.dm_hadr_automatic_seeding
```

## Автоматическое заполнение и вопросы производительности

SQL Server использует фиксированное количество потоков для автоматического заполнения. На первичном экземпляре SQL Server использует один поток на каждый LUN для считывания изменений. На вторичном экземпляре SQL Server использует один поток на каждый LUN для инициализации базы данных.

Установите флаг трассировки 9567 на первичной реплике для включения сжатия потока данных во время автоматического заполнения. Это позволит значительно сократить время передачи автоматического заполнения, однако при этом будет увеличена загрузка ЦП. Дополнительные сведения см. в разделе [Tune compression for availability group](../../../database-engine/availability-groups/windows/tune-compression-for-availability-group.md) (Настройка сжатия для группы доступности). 


## Когда не следует использовать автоматическое заполнение

В некоторых случаях автоматическое заполнение может оказаться неоптимальным решением для инициализации вторичной реплики. Во время автоматического заполнения SQL Server выполняет резервное копирование по сети для инициализации. Этот процесс может быть медленным, если размер баз данных слишком велик или вторичная реплика является удаленной. В ходе резервного копирования нельзя усекать журнал транзакций для этих баз данных, поэтому длительная инициализация в базе данных может привести к значительному увеличению размера журнала транзакций.
Перед добавлением базы данных в группу доступности с помощью автоматического заполнения нужно оценить размер базы данных, объем загрузки и расстояние между репликами.

## Ресурсы

[CREATE AVAILABILITY GROUP (Transact-SQL)
-](https://msdn.microsoft.com/library/ff878399.aspx)

[Руководство по мониторингу и устранению неполадок в группах доступности AlwaysOn](http://technet.microsoft.com/library/dn135328.aspx)
