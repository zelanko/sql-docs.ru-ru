---
title: Установка аздата с помощью установщика в Linux
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство аздата для установки (предварительной [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] версии) и управления им с помощью установщика (Linux).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e11e4851294ac8ffd8efa66e2156dcd47bce3aa0
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160684"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Установка `azdata` для управления [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как `azdata` установить версию-кандидат для кластера больших данных SQL Server 2019 в Linux. Перед тем как эти диспетчеры пакетов были доступны, `azdata` установка `pip`обязательно.

Диспетчеры пакетов предназначены для различных операционных систем и дистрибутивов.

- Для Linux (Ubuntu) [установите `azdata` с `apt` ](#azdata-apt)

В настоящее время нет диспетчеров пакетов для установки `azdata` в других операционных системах или дистрибутивах. Сведения об этих платформах см. в разделе [Install `azdata` без диспетчера пакетов](./deploy-install-azdata.md).

## <a id="linux"></a>Установка `azdata` для Linux

`azdata`пакет установки доступен для Ubuntu с `apt`.

### <a id="azdata-apt"></a>Установка `azdata` с помощью apt (Ubuntu)

>[!NOTE]
>`azdata` Пакет не использует системный Python, вместо этого устанавливает собственный интерпретатор Python.

1. Получение пакетов, необходимых для процесса установки:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Скачайте и установите ключ подписывания:

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add –
    ```

3. Добавьте сведения о репозитории: `azdata`

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
    ```

4. Обновите сведения о репозитории и установите `azdata`:

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Проверьте установку:

    ```bash
    azdata --version
    ```

### <a name="update"></a>Обновление

Только `azdata` обновление:

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Удаление

1. Удаление с помощью apt-get Remove:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Удалите сведения о репозитории: `azdata`

    >[!NOTE]
    >Этот шаг не требуется, если вы планируете установку `azdata` в будущем

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Удалите ключ подписывания:

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Удалите все ненужные зависимости, установленные с помощью Аздата CLI:

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]что такое?](big-data-cluster-overview.md).
