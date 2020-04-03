---
title: Управление группой доступности для SQL Server на Linux
description: В этой статье описывается, как провести последовательное обновление с помощью экземпляров SQL Server в Linux с группами доступности. Перед обновлением ознакомьтесь с рекомендациями.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 59e2f6c4321b1ccd90a66dd8e7466a3e0ccb490e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80216823"
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Управление группами доступности Always On на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>Обновление группы доступности

Перед обновлением группы доступности ознакомьтесь с шаблонами и рекомендациями по [обновлению экземпляров реплики группы доступности](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

В следующих разделах объясняется, как провести последовательное обновление с помощью экземпляров SQL Server в Linux с группами доступности. 

### <a name="upgrade-steps-on-linux"></a>Этапы обновления в Linux

Если реплики группы доступности находятся в экземплярах SQL Server на Linux, группа доступности может иметь тип кластера `EXTERNAL` или `NONE`. Группа доступности, управляемая диспетчером кластеров, помимо отказоустойчивого кластера Windows Server (WSFC), — это `EXTERNAL`. Примером внешнего диспетчера кластера является Pacemaker с Corosync. Группа доступности без диспетчера кластеров имеет тип кластера `NONE`. Действия по обновлению относятся только к группам доступности типа кластера `EXTERNAL` или `NONE`.

Порядок, в котором происходит обновление экземпляров, зависит от того, является ли их роль вторичной и независимо от того, размещены они в синхронной или асинхронной реплике. Сначала обновите экземпляры SQL Server, на которых размещаются асинхронные вторичные реплики. Затем обновите экземпляры, на которых размещены синхронные вторичные реплики. 

   >[!NOTE]
   >Если группа доступности содержит только асинхронные реплики, во избежание потери данных измените одну реплику на синхронную и подождите, пока она не будет синхронизирована. Затем обновите эту реплику.
   
Прежде чем начать, создайте резервную копию каждой базы данных.

1. Остановите ресурс на узле, на котором размещена вторичная реплика, предназначенная для обновления.
   
   Перед выполнением команды обновления следует завершить работу ресурса, чтобы кластер не вел его мониторинг и не регистрировал излишний сбой. В следующем примере на узле добавляется ограничение расположения, которое приведет к остановке ресурса. Обновите `ag_cluster-master`, указав имя ресурса, и `nodeName1`, указав узел, на котором размещена реплика, предназначенная для обновления.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. Обновите SQL Server на вторичной реплике.

   В следующем примере выполняется обновление пакетов `mssql-server` и `mssql-server-ha`.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. Удалите ограничение расположения.

   Перед выполнением команды обновления следует завершить работу ресурса, чтобы кластер не вел его мониторинг и не регистрировал излишний сбой. В следующем примере на узле добавляется ограничение расположения, которое приведет к остановке ресурса. Обновите `ag_cluster-master`, указав имя ресурса, и `nodeName1`, указав узел, на котором размещена реплика, предназначенная для обновления.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Рекомендуется убедиться, что ресурс запущен (с помощью команды `pcs status`), а вторичная реплика была подключена и синхронизирована после обновления.

1. После обновления всех вторичных реплик вручную отработайте отказ на одну из синхронных вторичных реплик.

   Для групп доступности с типом кластера `EXTERNAL` используйте средства управления кластерами для отработки отказа; группы доступности с типом кластера `NONE` должны использовать Transact-SQL для отработки отказа. 
   В следующем примере выполняется отработка отказа группы доступности с помощью средств управления кластером. Замените `<targetReplicaName>` на имя синхронной вторичной реплики, которая станет первичной.

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >Следующие шаги применимы только к группам доступности, у которых нет диспетчера кластеров.

   Если тип кластера группы доступности — `NONE`, нужна отработка отказа вручную. Последовательно выполните следующие шаги.

      а. Выполните следующую команду, чтобы превратить первичную реплику во вторичную. Замените `AG1` на имя группы доступности. Выполните команду Transact-SQL на экземпляре SQL Server, на котором размещена первичная реплика.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      b. Выполните следующую команду, чтобы превратить синхронную вторичную реплику в первичную. Выполните следующую команду Transact-SQL на целевом экземпляре SQL Server — экземпляре, на котором размещена синхронная вторичная реплика.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. После отработки отказа обновите SQL Server на старой первичной реплике, повторив предыдущую процедуру.

   В следующем примере выполняется обновление пакетов `mssql-server` и `mssql-server-ha`.

   ```bash
   # add constraint for the resource to stop on the upgraded node
   # replace 'nodename2' with the name of the cluster node targeted for upgrade
   pcs constraint location ag_cluster-master avoids nodeName2
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   
   ```bash
   # upgrade mssql-server and mssql-server-ha packages
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```

   ```bash
   # remove the constraint; make sure the resource is started and replica is connected and synchronized
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```

1. Для групп доступности с внешним диспетчером кластеров, где тип кластера — EXTERNAL, снимите ограничение расположения, которое было вызвано отработкой отказа вручную. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Возобновите перемещение данных для только что обновленной вторичной реплики — бывшей первичной реплики. Этот шаг необходим, если экземпляр более поздней версии SQL Server передает блоки журнала в экземпляр более ранней версии в группе доступности. Выполните следующую команду на новой вторичной реплике (которая ранее была первичной).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

После обновления всех серверов можно выполнить отработку отказа. При необходимости выполните отработку отказа на первоначальную основную реплику. 

## <a name="drop-an-availability-group"></a>Удаление группы доступности

Для удаления группы доступности используйте команду [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Если тип кластера — `EXTERNAL` или `NONE`, выполните команду на каждом экземпляре SQL Server, на котором размещена реплика. Например, следующая команда удаляет группу доступности с именем `group_name`.

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Дальнейшие действия

[Настройка кластера Red Hat Enterprise Linux для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка кластера SUSE Linux Enterprise Server для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
