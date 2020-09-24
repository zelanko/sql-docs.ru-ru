---
title: Установка azdata с помощью yum
titleSuffix: ''
description: Узнайте, как установить средство azdata с помощью yum.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eae81ccee65899335b161b3a32fbb260d0a8517a
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914902"
---
# <a name="install-azdata-with-yum"></a>Установка `azdata` с помощью yum

Для дистрибутивов Linux с `yum` существует пакет для `azdata-cli`. Пакет CLI протестирован для версий Linux, которые используют `yum`, а именно:

- RHEL 7, RHEL 8


[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-yum"></a>Установка с помощью yum

>[!IMPORTANT]
> Пакет RPM Azure для `azdata-cli` зависит от пакета python3. В вашей системе может быть установлена более ранняя версия Python, чем *требуемая версия 3.6.x*. Если для вас это важно, найдите другой пакет python3 или выполните инструкции по установке вручную с помощью [`pip`](../install/deploy-install-azdata-pip.md).

1. Импорт ключа репозитория Майкрософт

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Создание сведений о локальном репозитории

   Для клиента RHEL 7 выполните:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```
  
   Для клиента RHEL 8 выполните:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/prod.repo
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

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Использование azdata со [службами данных с поддержкой Azure Arc](/azure/azure-arc/data/)
