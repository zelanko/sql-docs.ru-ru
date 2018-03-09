---
title: "Настройка группы доступности SQL Server для чтения шкалы для Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: 460eb7ca3163a9a4ca8d53a24fec143f32b701e6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Настройка группы доступности SQL Server для чтения шкалы в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Можно настроить SQL Server всегда в группе доступности (AG) для рабочих нагрузок чтения масштабирования на платформе Linux. Существует два типа архитектур для групп доступности. Архитектура высокого уровня доступности использует диспетчер кластеров для обеспечения Улучшенная непрерывность бизнеса. Эта архитектура также могут включать шкалы чтения реплик. Создание архитектуры высокого уровня доступности — [настройки SQL Server группы доступности AlwaysOn для обеспечения высокой доступности в Linux](sql-server-linux-availability-group-configure-ha.md). Другие архитектура поддерживает только чтение шкалы рабочих нагрузок. В этой статье описывается создание группы Доступности без диспетчер кластеров для рабочих нагрузок чтения шкалы. Эта архитектура предоставляет чтения масштабирования только. Он не обеспечивает высокий уровень доступности.

>[!NOTE]
>Группа доступности с `CLUSTER_TYPE = NONE` могут включать реплики, размещенные на платформах операционных систем. Он не может поддерживать высокий уровень доступности. 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Создание группы Доступности

Создание группы Доступности. Set `CLUSTER_TYPE = NONE`. Кроме того, задать каждой реплики с `FAILOVER_MODE = NONE`. Клиентские приложения, аналитики и отчетности рабочих нагрузок может напрямую подключаться к баз данных-получателей. Также можно создать список маршрутизации только для чтения. Подключения к первичной реплике вперед чтения запросов на подключение к каждой из вторичных реплик в списке маршрутизации в циклического перебора.

Следующий сценарий Transact-SQL создает группы Доступности с именем `ag1`. Сценарий настраивает реплик группы Доступности с `SEEDING_MODE = AUTOMATIC`. Этот параметр задан, то SQL Server для автоматического создания базы данных на каждом сервере-получателе после его добавления к группе Доступности. Обновите следующий сценарий для вашей среды. Замените `<node1>` и `<node2>` значения с именами экземпляров SQL Server, на которых размещены реплики. Замените `<5022>` значение с портом, задать для конечной точки. Запустите следующий сценарий Transact-SQL в первичной реплике SQL Server:

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH ( 
            ENDPOINT_URL = N'tcp://<node2>:<5022>', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>Присоединение дополнительных серверов SQL к группе Доступности

Следующий сценарий Transact-SQL сервер присоединяет к группе Доступности с именем `ag1`. Обновите скрипт для вашей среды. На каждой из вторичных реплик SQL Server выполните следующий сценарий Transact-SQL для присоединения группы Доступности:

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Этой группы Доступности не конфигурации высокой доступности. Если требуется высокий уровень доступности, следуйте инструкциям в [Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md). В частности, создание группы Доступности с `CLUSTER_TYPE=WSFC` (в Windows) или `CLUSTER_TYPE=EXTERNAL` (в Linux). Затем интеграция с диспетчером кластера с помощью отказоустойчивых либо Windows Server в Windows или Pacemaker в Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Подключения к вторичным репликам только для чтения

Существует два способа подключения к вторичным репликам только для чтения. Приложения могут подключаться непосредственно к экземпляру SQL Server, на котором размещена вторичная реплика и запросы к базам данных. Они также могут использовать маршрутизацию только для чтения, которая требует прослушивателя.

* [Вторичные реплики для чтения](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Маршрутизация только для чтения](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Отработку отказа первичной реплики в группе доступности чтения шкалы

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Следующие шаги

* [Настройка распределенной группы доступности](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [Дополнительные сведения о группах доступности](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [Выполнить принудительную отработку отказа вручную](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

