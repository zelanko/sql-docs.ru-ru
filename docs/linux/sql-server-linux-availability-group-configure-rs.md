---
title: "Настройка группы доступности чтения шкалы для SQL Server для Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 10/20/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: 84fe8851a6ff3ad71e9ad9007bddc8715efc8829
ms.sourcegitcommit: c41e1bf5a53e96855b4424de4e0897153070bb28
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2017
---
# <a name="configure-a-read-scale-availability-group-for-sql-server-on-linux"></a>Настройка группы доступности чтения шкалы для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Можно настроить группу доступности чтения шкалы для SQL Server в Linux. Существует два архитектуры для группы доступности. Архитектура высокого уровня доступности использует диспетчер кластеров для обеспечения Улучшенная непрерывность бизнеса. Эта архитектура также могут включать шкалы чтения реплик. Создание архитектуры высокого уровня доступности — [Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md).

В этом документе объясняется, как создать группу доступности чтения масштаб без диспетчера кластеров. Эта архитектура предоставляет чтения масштабирования только. Он не обеспечивает высокий уровень доступности.

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Создание группы доступности

Создайте группу доступности. Set `CLUSTER_TYPE = NONE`. Кроме того, задать каждой реплики с `FAILOVER_MODE = NONE`. Клиентские приложения, аналитики и отчетности рабочих нагрузок может напрямую подключаться к баз данных-получателей. Также можно создать список маршрутизации только для чтения. Подключения к первичной реплике вперед чтения запросов на подключение к каждой из вторичных реплик в списке маршрутизации в циклического перебора.

Следующий сценарий Transact-SQL создает группу доступности с именем `ag1`. Сценарий настраивает реплики группы доступности с `SEEDING_MODE = AUTOMATIC`. Этот параметр задан, то SQL Server для автоматического создания базы данных на каждом сервере-получателе после его добавления в группу доступности. Обновите следующий сценарий для вашей среды. Замените `**<node1>**` и `**<node2>**` значения с именами экземпляров SQL Server, на которых размещены реплики. Замените `**<5022>**` значение с портом, задать для конечной точки. Запустите следующий сценарий Transact-SQL в первичной реплике SQL Server:

```SQL
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

Следующий сценарий Transact-SQL сервер присоединяется к группе доступности с именем `ag1`. Обновите скрипт для вашей среды. На каждой из вторичных реплик SQL Server выполните следующий скрипт Transact-SQL, чтобы присоединиться к группе доступности:

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Эта группа доступности не конфигурации высокой доступности. Если требуется высокий уровень доступности, следуйте инструкциям в [Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md). В частности, создайте группу доступности с `CLUSTER_TYPE=WSFC` (в Windows) или `CLUSTER_TYPE=EXTERNAL` (в Linux). Затем интеграция с диспетчером кластера с помощью отказоустойчивых либо Windows Server в Windows или Pacemaker в Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Подключения к вторичным репликам только для чтения

Существует два способа подключения к вторичным репликам только для чтения. Приложения могут подключаться непосредственно к экземпляру SQL Server, на котором размещена вторичная реплика и запросы к базам данных. Они также могут использовать маршрутизацию только для чтения, которая требует прослушивателя.

* [Вторичные реплики для чтения](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Маршрутизация только для чтения](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Отработку отказа первичной реплики в группе доступности чтения шкалы

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Следующие шаги

* [Настройка распределенной группы доступности](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [Дополнительные сведения о группах доступности](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [Выполнение принудительного перехода на другой ресурс вручную](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

