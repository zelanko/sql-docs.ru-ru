---
title: Установка azdata с помощью установщика в Linux
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство azdata для установки кластеров больших данных SQL Server и управления ими с помощью установщика (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9d8d4a34e89de7c136e1e80b43929531a2d10eba
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532074"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Установка `azdata` для управления [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается установка `azdata` для работы с кластерами больших данных SQL Server 2019 в Linux. До того как эти диспетчеры пакетов стали доступны, для установки `azdata` требовался `pip`.

Диспетчеры пакетов разработаны для разных операционных систем и дистрибутивов.

- В Windows и Linux (дистрибутив Ubuntu) для простоты можно выполнить установку с помощью [диспетчера пакетов](./deploy-install-azdata-installer.md).
- В Linux (Ubuntu) можно [установить `azdata` с помощью `apt`](#azdata-apt)

В настоящее время нет диспетчеров пакетов для установки `azdata` в других операционных системах или дистрибутивах. Об установке на этих платформах см. в разделе [Установка `azdata` без диспетчера пакетов](./deploy-install-azdata.md).

## <a id="linux"></a>Установка `azdata` в Linux

Пакет установки `azdata` доступен для Ubuntu с помощью `apt`.

### <a id="azdata-apt"></a>Установка `azdata` с помощью apt (Ubuntu)

>[!NOTE]
>Пакет `azdata` не использует системный Python и устанавливает собственный интерпретатор Python.

1. Получение пакетов, необходимых для процесса установки:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Загрузка и установка ключа подписывания:

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. Добавление сведений о репозитории `azdata`:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
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

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
