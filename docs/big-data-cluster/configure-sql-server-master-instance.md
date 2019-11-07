---
title: Настройка главного экземпляра SQL Server
titleSuffix: Configure SQL Server master instance of Big Data Cluster
description: Настройка главного экземпляра кластера больших данных SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 205f849310ffe2f6139e76783ba7fa6ac315b214
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532363"
---
# <a name="configure-master-instance-of-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Настройка главного экземпляра [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Настройте главный экземпляр [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)].

Нельзя настроить параметры конфигурации сервера для главного экземпляра SQL Server во время развертывания. В этой статье описывается временное решение для настройки таких параметров, как версия SQL Server, включение или отключение агента SQL Server, включение конкретных флагов трассировки или включение или отключение отзывов пользователей.

Чтобы изменить какие либо из этих параметров, выполните следующие действия.

1. Создайте пользовательский файл `mssql-custom.conf`, включающий нужные параметры. В следующем примере показано включение агента SQL, телеметрии, установка PID для выпуска Enterprise и включение флага трассировки 1204.

   ```
   [sqlagent]
   enabled=true
   
   [telemetry]
   customerfeedback=true
   userRequestedLocalAuditDirectory = /tmp/audit

   [DEFAULT]
   pid = Enterprise

   [traceflag]
   traceflag0 = 1204
   ```

1. Скопируйте файл `mssql-custom.conf` в каталог `/var/opt/mssql` в контейнере в `mssql-server` pod `master-0`. Замените `<namespaceName>` именем кластера больших данных.

   ```bash
   kubectl cp mssql-custom.conf master-0:/var/opt/mssql/mssql-custom.conf -c mssql-server -n <namespaceName>
   ```

1. Перезапустите экземпляр SQL Server.  Замените `<namespaceName>` именем кластера больших данных.

   ```bash
   kubectl exec -it master-0  -c mssql-server -n <namespaceName>-- /bin/bash
   supervisorctl restart mssql-server
   exit
   ```

> [!IMPORTANT]
> Если главный экземпляр SQL Server находится в конфигурации с группами доступности, скопируйте файл `mssql-custom.conf` во все pod `master`. Обратите внимание, что при каждом перезапуске будет происходить отработка отказа, поэтому необходимо убедиться, что это действие выполняется в период простоя.

## <a name="known-limitations"></a>Известные ограничения

- Для выполнения приведенных выше действий требуются разрешения администратора кластера Kubernetes.
- Невозможно изменить параметры сортировки сервера для главного экземпляра SQL Server кластера больших данных после развертывания.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании кластеров больших данных SQL Server см. в статье [Начало работы с кластерами больших данных SQL Server](deploy-get-started.md).