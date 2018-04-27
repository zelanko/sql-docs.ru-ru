---
title: Работы группы доступности SQL Server для Linux | Документы Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: Inactive
ms.openlocfilehash: 3242b0be9b907244f6e6809946bb38118592ec3c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Всегда работают в группах доступности в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>Обновление группы доступности

Перед обновлением группы доступности, просмотрите шаблоны и рекомендации по [обновление экземпляров реплики группы доступности](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Следующие разделы описывают выполнить последовательное обновление с экземплярами SQL Server в Linux с группами доступности. 

### <a name="upgrade-steps-on-linux"></a>Этапы обновления в Linux

Когда реплики доступности группы экземпляров SQL Server в Linux, тип кластера группы доступности — `EXTERNAL` или `NONE`. Группа доступности, которая находится под управлением диспетчера кластеров, помимо отказоустойчивого кластера (WSFC) является `EXTERNAL`. Pacemaker с Corosync примером может служить Диспетчер внешних кластера. Группа доступности с диспетчер кластера не имеет типа кластера `NONE` относятся приведенные ниже действия по обновлению для групп доступности кластера типа `EXTERNAL` или `NONE`.

Порядок, в котором обновление экземпляров зависит от Если соответствующая роль — получатель и ли они размещены реплики синхронным или асинхронным. Обновление экземпляров SQL Server, сначала размещения асинхронные вторичные реплики. Затем обновите экземплярах, где размещены синхронные вторичные реплики. 

   >[!NOTE]
   >Если группа доступности имеет только асинхронных реплик, чтобы избежать потери данных измените одной реплики на синхронный и подождите, пока он синхронизирован. Затем обновите этой реплики.
   
Прежде чем начать, создайте резервную копию каждой базы данных.

1. Остановите ресурса на узел, содержащий вторичную реплику, предназначенных для обновления.
   
   Перед выполнением команды обновления, остановите ресурс кластера не будет отслеживать ее и выполнять отработку отказа без необходимости. В следующем примере добавляется ограничение расположения на узле, который приведет к ресурса следует остановить. Обновление `ag_cluster-master` с именем ресурса и `nodeName1` с узла, на котором размещена реплика, предназначенных для обновления.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. Обновите SQL Server на вторичной реплике.

   В следующем примере выполняется обновление `mssql-server` и `mssql-server-ha` пакетов.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. Удалите ограничение расположения.

   Перед выполнением команды обновления, остановите ресурс кластера не будет отслеживать ее и выполнять отработку отказа без необходимости. В следующем примере добавляется ограничение расположения на узле, который приведет к ресурса следует остановить. Обновление `ag_cluster-master` с именем ресурса и `nodeName1` с узла, на котором размещена реплика, предназначенных для обновления.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Как рекомендуется обеспечить работу ресурс (с помощью `pcs status` команда) и Вторичная реплика подключена и синхронизировать состояние после обновления.

1. После обновления всех вторичных реплик вручную при сбое в один из синхронных вторичных реплик.

   Для группы доступности с `EXTERNAL` кластера типа, используйте средства управления кластером сбой over, группы доступности с `NONE` тип кластер должен использовать Transact-SQL для отработки отказа. 
   В следующем примере выполняется ресурс группы доступности с помощью средства управления кластером. Замените `<targetReplicaName>` с именем синхронной вторичной реплики, который станет основным:

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >Следующие шаги применяются только к группам доступности, у которых нет диспетчера кластеров.

   Если тип кластера группы доступности `NONE`вручную при сбое. Последовательно выполните следующие шаги.

      A. Следующая команда задает первичной реплики во вторичные. Замените `AG1` с именем группы доступности. Выполните команду Transact-SQL на экземпляре SQL Server, на котором размещена первичная реплика.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      Б. Следующая команда задает синхронная вторичная реплика к первичной. Выполните следующую команду Transact-SQL на целевом экземпляре SQL Server - экземпляр, на котором размещена вторичная реплика.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. После отработки отказа обновите SQL Server старой первичной реплике, повторив предыдущей процедуры.

   В следующем примере выполняется обновление `mssql-server` и `mssql-server-ha` пакетов.

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

1. Группы доступности с диспетчером внешнего - где тип кластера является ВНЕШНИМ, удалите ограничение расположение, которое было вызвано отработка отказа вручную. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Возобновление перемещения данных для только что обновленный вторичной реплики - бывшая первичная реплика. Этот шаг является обязательным, выше версии экземпляра SQL Server передачи блоков журнала ниже версии экземпляру в группе доступности. Выполните следующую команду на новую вторичную реплику (предыдущей первичной реплики).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

После обновления всех серверов, вы можете после сбоя. Переключение обратно на исходную первичную - при необходимости. 

## <a name="drop-an-availability-group"></a>Удалить группу доступности

Чтобы удалить группу доступности, запустите [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Если тип кластера `EXTERNAL` или `NONE` выполните команду на каждом экземпляре SQL Server, на котором размещена реплика. Например, чтобы удалить группу доступности с именем `group_name` выполните следующую команду:

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Следующие шаги

[Настройка Red Hat Enterprise Linux кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка SUSE Linux Enterprise Server кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
