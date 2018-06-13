---
title: Настройка группы доступности SQL Server для чтения и масштабирования в Windows | Документы Майкрософт
description: ''
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.reviewer: ''
ms.date: 05/24/2018
ms.topic: conceptual
ms.prod: sql
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.openlocfilehash: de62bd96371e93e9491b9c781da3b41f7086dc75
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768350"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-windows"></a>Настройка группы доступности SQL Server для чтения и масштабирования в Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Группу доступности AlwaysOn SQL Server для рабочих нагрузок для чтения и масштабирования можно настроить в Windows. Существует два типа архитектур для групп доступности. Архитектура для высокого уровня доступности использует диспетчер кластера для улучшенного обеспечения непрерывности бизнеса и может содержать доступные для чтения вторичные реплики. Сведения о создании архитектуры высокого уровня доступности см. в статье [Создание и настройка групп доступности в Windows](creation-and-configuration-of-availability-groups-sql-server.md). Другая архитектура поддерживает только рабочие нагрузки для чтения и масштабирования. В этой статье описывается создание группы доступности для рабочих нагрузок чтения и масштабирования без диспетчера кластеров. Эта архитектура обеспечивает только чтение и масштабирование. Она не поддерживает высокий уровень доступности.

>[!NOTE]
>В группу доступности с `CLUSTER_TYPE = NONE` могут входить реплики, размещенные на различных платформах операционных систем. Она не поддерживает высокий уровень доступности. Сведения об ОС Linux см. в статье [Настройка группы доступности SQL Server для чтения и масштабирования в Linux](../../../linux/sql-server-linux-availability-group-configure-rs.md).

[!INCLUDE [Create prerequisites](../../../includes/ss-availability-group-rs-prereq.md)]

## <a name="create-the-ag"></a>Создание группы доступности

Создайте группу доступности. Задайте `CLUSTER_TYPE = NONE`. Кроме того, задайте для каждой реплики `FAILOVER_MODE = NONE`. Клиентские приложения с рабочими нагрузками в области аналитики и отчетности могут напрямую подключаться к базам данных-получателям. Также можно создать список маршрутизации только для чтения. Подключения к первичной реплике будут переадресовывать запросы на подключение для чтения к каждой из содержащихся в нем вторичных реплик по принципу циклического перебора.

Следующий сценарий Transact-SQL создает группу доступности `ag1`. Сценарий настраивает реплики группы доступности с параметром `SEEDING_MODE = AUTOMATIC`. Если этот параметр задан, SQL Server будет автоматически создавать базы данных на каждом сервере-получателе после его добавления в группу доступности. Обновите следующий сценарий для своей среды. Замените значения `<node1>` и `<node2>` на имена экземпляров SQL Server, где размещаются реплики. Замените значение `<5022>` на порт, заданный для конечной точки. Выполните следующий сценарий Transact-SQL на первичной реплике SQL Server:

```sql
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

```sql
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);

ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../../../includes/ss-availability-group-rs-postactivity.md)]

У этой группы доступности нет конфигурации высокого уровня доступности. Если вам требуется высокий уровень доступности, следуйте инструкциям в статьях [Настройка группы доступности AlwaysOn для SQL Server в Linux](../../../linux/sql-server-linux-availability-group-configure-ha.md) или [Создание и настройка групп доступности в Windows](creation-and-configuration-of-availability-groups-sql-server.md).

## <a name="connect-to-read-only-secondary-replicas"></a>Подключение к вторичным репликам только для чтения

Существует два способа подключения к вторичным репликам только для чтения. Приложения могут подключаться непосредственно к экземпляру SQL Server, на котором размещена вторичная реплика, и отправлять запросы к базам данных. Они также могут использовать маршрутизацию только для чтения, для которой требуется прослушиватель.

* [Доступные для чтения вторичные реплики](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Маршрутизация только для чтения](listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Отработка отказа первичной реплики в группе доступности для чтения и масштабирования

[!INCLUDE[Force failover](../../../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Следующие шаги

* [Настройка распределенной группы доступности](distributed-availability-groups-always-on-availability-groups.md)
* [Дополнительные сведения о группах доступности](overview-of-always-on-availability-groups-sql-server.md)
* [Выполнение принудительного перехода на другой ресурс вручную](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)
