---
title: Настройка группы доступности SQL Server для чтения и масштабирования в Linux
titleSuffix: SQL Server
description: Сведения о настройке SQL Server всегда в группе доступности (AG) для рабочих нагрузок чтения и масштабирования в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.openlocfilehash: 60cdef13ec46ab1f859d17f724863f67939e6b6f
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206500"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Настройка группы доступности SQL Server для чтения и масштабирования в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Вы можете настроить SQL Server всегда в группе доступности (AG) для рабочих нагрузок чтения и масштабирования в Linux. Существует два типа архитектур для групп доступности. Архитектура для обеспечения высокой доступности диспетчер кластеров использует для предоставления Улучшенная непрерывность работы. Эта архитектура также могут включать реплик для чтения и масштабирования. Чтобы создать архитектура высокого уровня доступности, см. в разделе [настроить SQL Server группы доступности AlwaysOn для обеспечения высокой доступности в Linux](sql-server-linux-availability-group-configure-ha.md). Другая архитектура поддерживает только рабочие нагрузки для чтения и масштабирования. В этой статье описывается создание группы доступности для рабочих нагрузок чтения и масштабирования без диспетчера кластеров. Эта архитектура обеспечивает только чтение и масштабирование. Она не поддерживает высокий уровень доступности.

> [!NOTE]
> В группу доступности с `CLUSTER_TYPE = NONE` могут входить реплики, размещенные на различных платформах операционных систем. Она не поддерживает высокий уровень доступности. 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Создание группы доступности

Создайте группу доступности. Задайте `CLUSTER_TYPE = NONE`. Кроме того, задайте для каждой реплики `FAILOVER_MODE = MANUAL`. Клиентские приложения с рабочими нагрузками в области аналитики и отчетности могут напрямую подключаться к базам данных-получателям. Также можно создать список маршрутизации только для чтения. Подключения к первичной реплике будут переадресовывать запросы на подключение для чтения к каждой из содержащихся в нем вторичных реплик по принципу циклического перебора.

Следующий сценарий Transact-SQL создает группу доступности `ag1`. Сценарий настраивает реплики группы доступности с параметром `SEEDING_MODE = AUTOMATIC`. Если этот параметр задан, SQL Server будет автоматически создавать базы данных на каждом сервере-получателе после его добавления в группу доступности. Обновите следующий сценарий для своей среды. Замените значения `<node1>` и `<node2>` на имена экземпляров SQL Server, где размещаются реплики. Замените значение `<5022>` на порт, заданный для конечной точки. Выполните следующий сценарий Transact-SQL на первичной реплике SQL Server:

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

### <a name="join-secondary-sql-servers-to-the-ag"></a>Присоединение дополнительных серверов SQL к группе доступности

Следующий сценарий Transact-SQL создает группу доступности `ag1`. Обновите сценарий для своей среды. На каждой вторичной реплике SQL Server выполните следующий сценарий Transact-SQL для присоединения группы доступности:

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

У этой группы доступности нет конфигурации высокого уровня доступности. Если требуется высокий уровень доступности, следуйте инструкциям в [Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md). В частности, для создания группы Доступности с `CLUSTER_TYPE=WSFC` (в Windows) или `CLUSTER_TYPE=EXTERNAL` (в Linux). Затем интеграция с диспетчером кластера с помощью либо отказоустойчивому кластеру Windows на Windows или Pacemaker в Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Подключение к вторичным репликам только для чтения

Существует два способа подключения к вторичным репликам только для чтения. Приложения могут подключаться непосредственно к экземпляру SQL Server, на котором размещена вторичная реплика, и отправлять запросы к базам данных. Они также могут использовать маршрутизацию только для чтения, для которой требуется прослушиватель.

* [Доступные для чтения вторичные реплики](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Маршрутизация только для чтения](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Отработка отказа первичной реплики в группе доступности для чтения и масштабирования

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Следующие шаги

* [Настройка распределенной группы доступности](../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)
* [Дополнительные сведения о группах доступности](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
* [Выполнение принудительного перехода на другой ресурс вручную](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)
