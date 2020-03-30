---
title: Установка azdata с помощью yum
titleSuffix: SQL Server big data clusters
description: Сведения о том, как установить средство azdata для установки Кластеров больших данных и управления ими с помощью yum.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cf6e061b0ca4fca7c843575a87038a801ab8f758
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75728555"
---
# <a name="install-azdata-with-yum"></a>Установка `azdata` с помощью yum

Для дистрибутивов Linux с `yum` существует пакет для `azdata-cli`. Пакет CLI протестирован для версий Linux, которые используют `yum`, а именно:

- RHEL 7, RHEL 8


[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-yum"></a>Установка с помощью yum

>[!IMPORTANT]
> Пакет RPM Azure для `azdata-cli` зависит от пакета python3. В вашей системе может быть установлена более ранняя версия Python, чем *требуемая версия 3.6.x*. Если для вас это важно, найдите другой пакет python3 или выполните инструкции по установке вручную с помощью [`pip`](deploy-install-azdata-pip.md).

1. Импорт ключа репозитория Майкрософт

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Создание сведений о локальном репозитории

   Для клиента RHEL 7 выполните:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo
   ```
  
   Для клиента RHEL 8 выполните:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo
   ```

1. Установка с помощью команды `yum install`

   ```bash
   sudo yum install azdata-cli
   ```

## <a name="verify-install"></a>Проверка установки

```
azdata
azdata --version
```

## <a name="update"></a>Update

Выполните обновление `azdata-cli` с помощью команды `yum update`.

```bash
sudo yum update azdata-cli
```

## <a name="uninstall"></a>Удаление

1. Удалите пакет из системы.

   ```bash
   sudo yum remove azdata-cli
   ```

1. Если вы не планируете переустанавливать `azdata-cli`, удалите сведения о репозитории.

   ```bash
   sudo rm /etc/yum.repos.d/azdata-cli.repo
   ```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
