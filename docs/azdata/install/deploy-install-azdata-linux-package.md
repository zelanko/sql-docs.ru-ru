---
title: Установка azdata с помощью установщика в Linux
titleSuffix: ''
description: Узнайте, как установить средство azdata с помощью установщика (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2dc1c3d58ee5f7b6ea032a2e41f7c18431229881
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914964"
---
# <a name="install-azdata-with-apt"></a>Установка `azdata` с помощью apt

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/azdata.md)]

В этой статье описывается порядок установки `azdata` в Linux. До того как эти диспетчеры пакетов стали доступны, для установки `azdata` требовался `pip`.

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-azdata-for-linux"></a><a id="linux"></a>Установка `azdata` в Linux

Пакет установки `azdata` доступен для Ubuntu с помощью `apt`.

### <a name="install-azdata-with-apt-ubuntu"></a><a id="azdata-apt"></a>Установка `azdata` с помощью apt (Ubuntu)

>[!NOTE]
>Пакет `azdata` не использует системный Python и устанавливает собственный интерпретатор Python.

1. Получение пакетов, необходимых для процесса установки:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl wget software-properties-common apt-transport-https lsb-release -y
    ```

2. Загрузка и установка ключа подписывания:

    ```bash
    curl -sL https://packages.microsoft.com/keys/microsoft.asc |
    gpg --dearmor |
    sudo tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
    ```

3. Добавьте сведения о репозитории `azdata`.

   Для запуска клиента Ubuntu 16.04 выполните:
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
    ```

   Для запуска клиента Ubuntu 18.04 выполните:
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/prod.list)"
    ```

4. Обновление сведений о репозитории и установка `azdata`:

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Проверка установки:

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Обновление только `azdata`:

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Удаление

1. Удаление с помощью apt-get remove:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Удаление сведений о репозитории `azdata`:

    >[!NOTE]
    >Этот шаг не требуется, если вы планируете установить `azdata` в будущем.

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Удаление ключа подписывания:

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Удаление всех ненужных зависимостей, установленных с помощью CLI Azdata:

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Использование azdata со [службами данных с поддержкой Azure Arc](/azure/azure-arc/data/)