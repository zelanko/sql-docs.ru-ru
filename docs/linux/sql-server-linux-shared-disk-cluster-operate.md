---
title: Работа экземпляра отказоустойчивого кластера — SQL Server на Linux
description: В этой статье описывается работа экземпляра отказоустойчивого кластера (FCI) SQL Server на Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 0da3a3225e3ef47bd4a38d1ccbcc2d074d543a55
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154571"
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Работа экземпляра отказоустойчивого кластера — SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается работа экземпляра отказоустойчивого кластера (FCI) SQL Server на Linux. Если вы еще не создали экземпляр FCI SQL Server на Linux, см. статью [Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure.md). 

## <a name="failover"></a>Отработка отказа

Отработка отказа для FCI аналогична работе отказоустойчивого кластера Windows Server (WSFC). Если на узле кластера, где размещен экземпляр FCI, возникают какие-либо сбои, экземпляр FCI должен автоматически выполнить отработку отказа на другой узел. В отличие от WSFC здесь невозможно задать предпочтительных владельцев, поэтому Pacemaker выбирает узел, который будет новым узлом для экземпляра FCI.

Иногда может потребоваться вручную перевести экземпляр FCI на другой узел. Этот процесс отличается от действий с экземплярами FCI в кластере WSFC. В кластере WSFC отработка отказа ресурсов выполняется на уровне роли. В Pacemaker вы выбираете ресурс для перемещения и, поскольку предполагается, что все ограничения верны, будут перемещены и все остальные компоненты. 

Способ отработки отказа зависит от дистрибутива Linux. Следуйте инструкциям для дистрибутива Linux.

- [RHEL или Ubuntu](#manual-failover-rhel-or-ubuntu)
- [SLES](#manual-failover-sles)

## <a name="manual-failover-rhel-or-ubuntu"></a>Отработка отказа вручную (RHEL или Ubuntu)

Чтобы выполнить отработку отказа вручную, на серверах Red Hat Enterprise Linux (RHEL) или Ubuntu выполните приведенные далее действия.
1.  Выполните следующую команду: 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName> — имя ресурса Pacemaker для экземпляра FCI SQL Server.

   \<NewHostNode> — имя узла кластера, на котором будет размещен экземпляр FCI. 

   Подтверждения выводиться не будут.

2.  Во время отработки отказа вручную Pacemaker создает ограничение расположения для ресурса, выбранного для перемещения. Чтобы просмотреть это ограничение, выполните команду `sudo pcs constraint`.

3.  После завершения отработки отказа удалите ограничение, выполнив команду `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName> — имя ресурса Pacemaker для экземпляра FCI. 

## <a name="manual-failover-sles"></a>Отработка отказа вручную (SLES)


Чтобы выполнить отработку отказа экземпляра FCI SQL Server вручную, в Suse Linux Enterprise Server (SLES) запустите команду `migrate`. Пример:

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName> — имя ресурса для экземпляра отказоустойчивого кластера. 

\<NewHostNode> — имя нового узла назначения. 


<!---

|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)

--->

## <a name="next-steps"></a>Next Steps

- [Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
