---
title: Работы группы доступности SQL Server в Linux | Документация Майкрософт
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 6a24d1cb2e9bff3555aa24eb0df079bc2894ec79
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984302"
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Всегда работают с группами доступности в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>Обновление группы доступности

Перед обновлением группы доступности, просмотрите шаблоны и приемы по [обновление экземпляров реплики группы доступности](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Ниже описаны способы выполнения последовательного обновления с экземплярами SQL Server в Linux с помощью групп доступности. 

### <a name="upgrade-steps-on-linux"></a>Этапы обновления на платформе Linux

Если реплики группы доступности на экземплярах SQL Server в Linux, тип кластера группы доступности — `EXTERNAL` или `NONE`. Группы доступности, которая управляется диспетчером кластера, кроме отказоустойчивого кластера Windows Server (WSFC) — `EXTERNAL`. Pacemaker с использованием Corosync является примером Диспетчер внешних кластера. В группе доступности без диспетчера кластеров задан тип кластера `NONE` действия по обновлению, описанную в этой статье предназначены для групп доступности типа кластера `EXTERNAL` или `NONE`.

Порядок, в котором выполняется обновление экземпляров зависит время ли их роли, вторичная реплика и ли они размещены реплики синхронной или асинхронной. Обновление экземпляров SQL Server, на которых размещены сначала асинхронные вторичные реплики. Затем обновление экземпляров, на которых размещены синхронных вторичных реплик. 

   >[!NOTE]
   >Если группа доступности имеет только асинхронных реплик, чтобы избежать потери данных изменение одной из реплик на синхронный и подождите, пока он синхронизируется. Затем обновите эту реплику.
   
Прежде чем начать, резервную копию каждой базы данных.

1. Остановка ресурса в узла, на котором размещается вторичная реплика, предназначенных для обновления.
   
   Перед выполнением обновления команды остановки ресурса, кластер не будет отслеживать его и отработки ее без необходимости. В следующем примере добавляется ограничение расположения на узле, который приведет к ресурса следует остановить. Обновление `ag_cluster-master` с именем ресурса и `nodeName1` с узлом, на котором размещена реплика, предназначенных для обновления.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. Обновите SQL Server на вторичной реплике.

   В следующем примере обновляется `mssql-server` и `mssql-server-ha` пакетов.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. Удаление ограничения расположения.

   Перед выполнением обновления команды остановки ресурса, кластер не будет отслеживать его и отработки ее без необходимости. В следующем примере добавляется ограничение расположения на узле, который приведет к ресурса следует остановить. Обновление `ag_cluster-master` с именем ресурса и `nodeName1` с узлом, на котором размещена реплика, предназначенных для обновления.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Рекомендуется обеспечить наличие ресурса был запущен (с помощью `pcs status` команда) и Вторичная реплика подключена и синхронизированном состоянии после обновления.

1. После обновления все вторичные реплики, на другой ресурс вручную на один из синхронных вторичных реплик.

   Для групп доступности с `EXTERNAL` тип кластера, используйте средства управления кластером переход на другой over; группы доступности с `NONE` тип кластера следует использовать Transact-SQL для отработки отказа. 
   В следующем примере отработка отказа группы доступности с помощью средства управления кластером. Замените `<targetReplicaName>` именем синхронная вторичная реплика, которая станет основной группой:

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >Следующие шаги применяются только к группам доступности, у которых нет диспетчер кластеров.

   Если тип кластера группы доступности `NONE`вручную выполнить отработку отказа. Последовательно выполните следующие шаги.

      A. Следующая команда задает первичной реплики в дополнительный регион. Замените `AG1` с именем группы доступности. Выполните команду Transact-SQL на экземпляре SQL Server, на котором размещена первичная реплика.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      Б. Следующая команда задает синхронной вторичной реплики до первичной. Выполните следующую команду Transact-SQL на целевом экземпляре SQL Server - экземпляр, на котором размещается синхронная вторичная реплика.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. После отработки отказа обновите SQL Server в старой первичной реплике, повторив предыдущей процедуры.

   В следующем примере обновляется `mssql-server` и `mssql-server-ha` пакетов.

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

1. Для групп доступности с диспетчером внешнего - где тип кластера — EXTERNAL, удалить ограничение расположения, вызванное на другой ресурс вручную. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Возобновление перемещения данных для только что обновленный вторичной реплики - бывшая первичная реплика. Этот шаг является обязательным при выше версии экземпляра SQL Server передает блоков журнала на экземпляр версии ниже в группе доступности. Выполните следующую команду на новую вторичную реплику (прежнюю первичную реплику).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

После обновления всех серверов, можно восстановить размещение. При необходимости выполнить отработку отказа обратно на исходную первичную реплику. 

## <a name="drop-an-availability-group"></a>Удалить группу доступности

Чтобы удалить группу доступности, выполните [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Если тип кластера — `EXTERNAL` или `NONE` выполните команду на каждом экземпляре SQL Server, на котором размещена реплика. Например, чтобы удалить группу доступности с именем `group_name` выполните следующую команду:

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Следующие шаги

[Настройка кластера Red Hat Enterprise Linux, для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка кластера серверов SUSE Linux Enterprise для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
