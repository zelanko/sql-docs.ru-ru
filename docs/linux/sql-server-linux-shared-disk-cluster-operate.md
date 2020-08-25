---
title: Ручная отработка отказа экземпляра отказоустойчивого кластера — SQL Server на Linux
description: Сведения о том, как вручную отработать отказ экземпляра отказоустойчивого кластера на SQL Server на Linux, в особенности Red Hat Linux Enterprise, Ubuntu и Suse Linux Enterprise Server.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 2be454ad7d2ca85f1648ba7f98ea503627d6c437
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088762"
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Работа экземпляра отказоустойчивого кластера — SQL Server на Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

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

   \<FCIResourceName> — имя ресурса Pacemaker для экземпляра FCI SQL Server.

   \<NewHostNode> — имя узла кластера, на котором вы хотите разместить экземпляр FCI. 

   Подтверждения выводиться не будут.

2.  Во время отработки отказа вручную Pacemaker создает ограничение расположения для ресурса, выбранного для перемещения. Чтобы просмотреть это ограничение, выполните команду `sudo pcs constraint`.

3.  После завершения отработки отказа удалите ограничение, выполнив команду `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName> — имя ресурса Pacemaker для экземпляра FCI. 

## <a name="manual-failover-sles"></a>Отработка отказа вручную (SLES)


Чтобы выполнить отработку отказа экземпляра FCI SQL Server вручную, в Suse Linux Enterprise Server (SLES) запустите команду `migrate`. Пример:

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName> — имя ресурса для экземпляра отказоустойчивого кластера. 

\<NewHostNode> — имя нового узла назначения. 


<!---

|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)

--->

## <a name="next-steps"></a>Next Steps

- [Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
