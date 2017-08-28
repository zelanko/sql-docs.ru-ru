---
title: "Настройка группы доступности чтения горизонтального масштабирования для SQL Server в Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cf249ff8e6d2e82d1cf413bdec0272e3796b72cb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="configure-read-scale-out-availability-group-for-sql-server-on-linux"></a>Настройка группы доступности чтения горизонтального масштабирования для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Можно настроить группу доступности чтения горизонтального масштабирования для SQL Server в Linux. Существует два архитектуры для группы доступности. Объект *высокий уровень доступности* архитектура использует диспетчер кластеров для обеспечения Улучшенная непрерывность бизнеса. Эта архитектура также может включать реплики для чтения горизонтального масштабирования. Создание архитектуры высокого уровня доступности — [Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md).

В этом документе описывается процесс создания *чтения масштабирования* группы доступности без диспетчера кластеров. Эта архитектура предоставляет только чтения масштабирования только. Он не обеспечивает высокий уровень доступности.

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Создание группы доступности

Создайте группу доступности. Set `CLUSTER_TYPE = NONE`. Кроме того, задать каждой реплики с `FAILOVER_MODE = NONE`. Клиентские приложения, аналитики и отчетности рабочих нагрузок может напрямую подключаться к баз данных-получателей. Можно также создать список маршрутизации только для чтения. Подключения к первичной реплике вперед чтения запросов на подключение к каждой из вторичных реплик в списке маршрутизации в циклического перебора.

Следующий сценарий Transact-SQL создает имя группы доступности `ag1`. Сценарий настраивает реплики группы доступности с `SEEDING_MODE = AUTOMATIC`. Этот параметр задан, то SQL Server для автоматического создания базы данных на каждом сервере-получателе после его добавления в группу доступности. Обновите следующий сценарий для вашей среды. Замените `**<node1>**` и `**<node2>**` значения с именами экземпляров SQL Server, на которых размещены реплики. Замените `**<5022>**` с портом, задать для конечной точки. Выполните следующий запрос Transact-SQL в первичной реплике SQL Server:

```Transact-SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'**<node1>**' WITH (
            ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'**<node2>**' WITH ( 
            ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-availability-group"></a>Присоединение дополнительных серверов SQL к группе доступности

Следующий сценарий Transact-SQL сервер присоединяется к группе доступности с именем `ag1`. Обновите скрипт для вашей среды. На каждой из вторичных реплик SQL Server запустите следующий скрипт Transact-SQL присоединиться к группе доступности.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Это не конфигурации высокого уровня доступности, если требуется высокий уровень доступности, следуйте инструкциям в [Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md). В частности, создайте группу доступности с `CLUSTER_TYPE=WSFC` (в Windows) или `CLUSTER_TYPE=EXTERNAL` (в Linux) и интегрировать диспетчер кластеров - либо WSFC в Windows или Pacemaker в Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Подключения к вторичным репликам только для чтения

Существует два способа подключения к вторичным репликам только для чтения. Приложения могут подключаться непосредственно к экземпляру SQL Server, на котором размещена вторичная реплика и запросы к базам данных, или они могут использовать маршрутизацию только для чтения. Маршрутизация только для чтения требует прослушивателя.

[Вторичные реплики для чтения](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)

[Маршрутизация только для чтения](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-primary-replica-on-read-scale-out-availability-group"></a>Отработку отказа первичной реплики в группе доступности чтения масштабирования

Каждая группа доступности содержит только одну первичную реплику. Первичная реплика позволяет считывает и записывает. Чтобы изменить реплику, которая является основным, можно выполнить переход. В группе доступности для обеспечения высокой доступности диспетчера кластеров автоматизирует процесс перехода на другой ресурс. В группе доступности чтения масштабирования процесс перехода на другой ресурс вручную. Для отработки отказа первичной реплики в группе доступности чтения шкалы двумя способами.

- Принудительный вручную fail над с потерей данных

- Ручной отработки отказа без потери данных

### <a name="forced-fail-over-with-data-loss"></a>Принудительный переход на другой ресурс с потерей данных

Используйте этот метод, если первичная реплика недоступна и не может быть восстановлен. Можно найти дополнительные сведения о принудительной отработки отказа с потерей данных на [выполнения принудительной отработки отказа вручную](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).

Выполняйте переход с потерей данных, подключитесь к экземпляру SQL, в котором размещена целевая вторичная реплика, и выполните:
```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-fail-over-without-data-loss"></a>Ручной отработки отказа без потери данных

Используйте этот метод первичная реплика становится доступной, когда необходимо временно или навсегда изменения конфигурации и изменить экземпляр SQL Server, на котором размещена первичная реплика. Перед выдачей сбоя вручную через, убедитесь, целевая вторичная реплика в актуальном состоянии, таким образом, что без потери данных. 

Следующие шаги описывают, как отработка отказа без потери данных вручную:

1. Убедитесь в целевой вторичной реплики синхронной фиксацией.

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] MODIFY REPLICA ON N'**<node2>*' WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```
1. Обновление `required_synchronized_secondaries_to_commit`значение 1.

   Этот параметр обеспечивает все активные транзакции зафиксированы первичная реплика и хотя бы один синхронного сервера-получателя. Группа доступности готова для отработки отказа при СИНХРОНИЗАЦИИ synchronization_state_desc и sequence_number является одинаковым для обоих первичной и целевой вторичной реплики. Выполните этот запрос для проверки.

   ```Transact-SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

1. Понижение роли первичной реплики на вторичную реплику. После понижения роли первичной реплики, он доступен только для чтения. На экземпляре SQL Server размещается первичная реплика, чтобы обновить вторичную роль, выполните следующую команду:

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY); 
   ```

1. Повышение уровня целевая вторичная реплика к первичной. 

   ```Transact-SQL
   ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Для удаления группы доступности используйте [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Для группы доступности, созданных с помощью CLUSTER_TYPE NONE или внешний команда должна выполняться на всех репликах часть группы доступности.

## <a name="next-steps"></a>Следующие шаги

[Настройка распределенной группы доступности](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)

[Дополнительные сведения о группах доступности](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)


