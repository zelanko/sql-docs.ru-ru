---
title: Свойства конфигурации главного экземпляра SQL Server
titleSuffix: SQL Server big data clusters
description: Справочная статья по свойствам конфигурации главного экземпляра SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: rahul.ajmera
ms.date: 08/04/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 60888246623796d9b4d17c498da47ab4b6557cf2
ms.sourcegitcommit: 6ab28d954f3a63168463321a8bc6ecced099b247
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87790477"
---
# <a name="sql-server-master-instance-configuration-properties"></a>Свойства конфигурации главного экземпляра SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

## <a name="properties"></a>Свойства

Во время развертывания для главного экземпляра можно настроить следующие параметры SQL Server.

|Свойство|Параметры|
| --- | --- |
|`[sqlagent]`|`enabled = { true | false }` |
|`[telemetry]`|`customerfeedback = { true | false }` |
|`[telemetry]`|`userRequestedLocalAuditDirectory = </path/file>`|
|`[licensing]`| `pid = { Enterprise | Developer }`|
|`[traceflag]`|` traceflag<#> = <####>`|

### <a name="examples"></a>Примеры

В следующем примере показано включение агента SQL, телеметрии, установка PID для выпуска Enterprise и включение флага трассировки 1204.

```
[sqlagent]
enabled=true

[telemetry]
customerfeedback=true
userRequestedLocalAuditDirectory = /tmp/audit

[licensing]
pid = Enterprise

[traceflag]
traceflag0 = 1204
```

Инструкции см. в статье [Настройка главного экземпляра для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md).

## <a name="next-steps"></a>Дальнейшие шаги

[Настройка главного экземпляра [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md)
