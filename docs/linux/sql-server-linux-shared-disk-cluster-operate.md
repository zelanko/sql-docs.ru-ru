---
title: "Экземпляр отказоустойчивого кластера — SQL Server в Linux работать | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: aba3ca214a1ea96d18aa17285ed40235bf2f7bdb
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Работать экземпляр отказоустойчивого кластера — SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этой статье объясняется, как для работы SQL Server экземпляра отказоустойчивого кластера (FCI) в Linux. Если вы не создали отказоустойчивого Кластера SQL Server в Linux, см. раздел [настроить отказоустойчивый кластер — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md). 

## <a name="failover"></a>Отработка отказа

Отработка отказа для FCI похож на отказоустойчивом кластере Windows Server (WSFC). Если какая-либо сбоя узла кластера, на котором размещена FCI, FCI должен автоматически переключаться на другой узел. В отличие от WSFC нет возможности настроить предпочитаемых владельцев, чтобы Pacemaker выбирает узел, который будет входить в новый узел для FCI.

Бывают случаи, необходимо вручную перейти на другой узел в FCI. Процесс не так же, как экземпляры отказоустойчивого кластера в кластере WSFC. В кластере WSFC вы дублируете ресурсы на уровне роли. Выберите ресурс для перемещения в Pacemaker, и при условии, что все ограничения указаны правильно, все остальные переместит также. 

Способ отработки отказа зависит от дистрибутив Linux. Следуйте инструкциям для своего дистрибутива linux.

- [RHEL или Ubuntu](#rhelFailover)
- [SLES](#slesFailover)

## <a name = "#rhelFailover"></a>Отработка отказа вручную (RHEL или Ubuntu)

Чтобы выполнить отработку отказа вручную, onn Red Hat Enterprise Linux (RHEL) или Ubuntu серверов выполните следующие действия.
1.  Выполните следующую команду: 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName > — это имя ресурса Pacemaker для отказоустойчивого Кластера SQL Server.

   \<NewHostNode > — имя узла кластера, где будет размещаться FCI. 

   Вы не будете любое подтверждение.

2.  При отработке отказа вручную Pacemaker создается ограничение расположения ресурсов, которые были выбраны для перемещения вручную. Чтобы просмотреть это ограничение, запустите `sudo pcs constraint`.

3.  После отработки отказа, удалите это ограничение, выполнив `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName > — имя ресурса Pacemaker для FCI. 

## <a name = "#slesFailover"></a>Отработка отказа вручную (SLES)


В Suse Linux Enterprise Server (SLES), используйте `migrate` команда отказоустойчивого Кластера SQL Server, переход на другой ресурс вручную. Например:

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName > — имя ресурс для экземпляра отказоустойчивого кластера. 

\<NewHostNode > — имя нового узла назначения. 


<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
--->

## <a name="next-steps"></a>Следующие шаги

- [Настроить экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
