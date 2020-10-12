---
title: Установка azdata с помощью zypper
titleSuffix: ''
description: Узнайте, как установить средство azdata с помощью zypper.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ec87d5739e3707c056f7945a2c882eb00700464d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725268"
---
# <a name="install-azdata-with-zypper"></a>Установка `azdata` с помощью zypper

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Для дистрибутивов Linux с `zypper` существует пакет для `azdata-cli`. Пакет CLI протестирован для версий Linux, которые используют `zypper`, а именно:

- openSUSE Leap 42.2 и более поздних версий;
- SLES 12 SP 2 и более поздних версий.

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>Установка с помощью zypper

>[!IMPORTANT]
>Пакет RPM Azure для `azdata-cli` зависит от пакета python3. В вашей системе может быть установлена более ранняя версия Python, чем *требуемая версия 3.6.x*. Если для вас это важно, найдите другой пакет python3 или выполните инструкции по установке вручную с помощью [`pip`](../install/deploy-install-azdata-pip.md).

1. Установите зависимости, необходимые для установки `azdata-cli`.

   ```bash
   sudo zypper install -y curl
   ```

1. Импортируйте ключ репозитория Майкрософт.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Создайте сведения о локальном репозитории.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo
   ```

1. Установить службы `azdata-cli`.

   ```bash
   sudo zypper install --from packages-microsoft-com-mssql-server-2019 -y azdata-cli
   ```

## <a name="verify-install"></a>Проверка установки

```bash
azdata
azdata --version
```

## <a name="update"></a>Update

Выполните обновление `azdata-cli` с помощью команды `zypper update`.

```bash
sudo zypper refresh
sudo zypper update azdata-cli
```

## <a name="uninstall"></a>Удаление

Удалите пакет из системы.

```bash
sudo zypper removerepo azdata-cli
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Использование azdata со [службами данных с поддержкой Azure Arc](/azure/azure-arc/data/)