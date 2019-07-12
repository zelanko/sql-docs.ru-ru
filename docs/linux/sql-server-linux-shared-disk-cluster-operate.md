---
title: Работа экземпляра отказоустойчивого кластера — SQL Server на Linux
description: В этой статье объясняется, как для работы SQL Server экземпляра отказоустойчивого кластера (FCI) в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: cc0059f8e8dc43b2c65e432d7cdd56272218d36c
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833154"
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Работа экземпляра отказоустойчивого кластера — SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как для работы SQL Server экземпляра отказоустойчивого кластера (FCI) в Linux. Если вы не создали экземпляр отказоустойчивого Кластера SQL Server в Linux, см. в разделе [экземпляр Настройка отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md). 

## <a name="failover"></a>Отработка отказа

Отработка отказа для FCI похоже на отказоустойчивый кластер Windows Server (WSFC). Если узел кластера, размещение FCI испытывает определенные ошибки, FCI должен автоматически выполнить отработку отказа на другой узел. В отличие от кластера WSFC нет способа для задания предпочтительных владельцев, чтобы Pacemaker выбирает узел, который будет новым узлом для FCI.

Бывают случаи, может потребоваться вручную выполнить отказоустойчивого Кластера на другой узел. Процесс не таким же, как экземпляры отказоустойчивого кластера в кластере WSFC. В кластере WSFC выполняется отработка отказа ресурсов на уровне роли. В Pacemaker выберите ресурс для перемещения и при условии, что все ограничения заданы правильно, все остальное будет переместить также. 

Способ отработки отказа зависит от дистрибутива Linux. Следуйте инструкциям для дистрибутива linux.

- [RHEL или Ubuntu](#-manual-failover-rhel-or-ubuntu)
- [SLES](#-manual-failover-sles)

## <a name = "#-manual-failover-rhel-or-ubuntu"></a> На другой ресурс вручную (RHEL или Ubuntu)

Чтобы выполнить отработку отказа вручную, обновите Red Hat Enterprise Linux (RHEL) или на серверах Ubuntu выполните следующие действия.
1.  Выполните следующую команду: 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName > — имя ресурса Pacemaker для экземпляра отказоустойчивого Кластера SQL Server.

   \<NewHostNode > — имя узла кластера, который будет размещаться FCI. 

   Любое подтверждение не будет.

2.  Во время перехода на другой ресурс вручную Pacemaker создает ограничение расположения для ресурсов, которая была выбрана для перемещения вручную. Чтобы просмотреть это ограничение, выполните `sudo pcs constraint`.

3.  После завершения отработки отказа, необходимо удалить ограничение, выполнив `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName > — имя ресурса для экземпляра отказоустойчивого Кластера Pacemaker. 

## <a name = "#-manual-failover-sles"></a> На другой ресурс вручную (SLES)


В Suse Linux Enterprise Server (SLES), используйте `migrate` команду, чтобы вручную выполните отработку отказа экземпляра отказоустойчивого Кластера SQL Server. Пример:

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName > — это имя reource для экземпляра отказоустойчивого кластера. 

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
