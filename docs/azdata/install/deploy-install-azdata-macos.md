---
title: Установка azdata для macOS
titleSuffix: SQL Server big data clusters
description: Сведения о том, как установить средство azdata для установки кластеров больших данных и управления ими в macOS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6662a5ff7ced4c260e2b1a3fbd1efe5a285cf4a
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89734076"
---
# <a name="install-azdata-on-macos"></a>Установка `azdata` в macOS

`azdata-cli` можно установить на платформе macOS с помощью диспетчера пакетов Homebrew. Пакет CLI протестирован с macOS следующих версий: 
* 10.13 High Sierra;
* 10.14 Mojave;
* 10.15 Catalina.

## <a name="install-with-homebrew"></a>Установка с помощью Homebrew

```bash
brew tap microsoft/azdata-cli-release
brew update
brew install azdata-cli
```

>[!IMPORTANT]
>`azdata-cli` имеет зависимость от пакетов Homebrew `python3`, `freetds`, `unixodbc` и `zeromq`, поэтому устанавливает их автоматически. Для `azdata-cli` гарантируется совместимость с последними версиями этих зависимостей, опубликованными в Homebrew.

## <a name="verify-install"></a>Проверка установки

```bash
azdata
azdata --version
```

## <a name="update"></a>Update

Обновите сведения о локальном репозитории, а затем — сам пакет `azdata-cli`.

```bash
brew tap microsoft/azdata-cli-release
brew update
brew upgrade azdata-cli
```

## <a name="uninstall"></a>Удаление

Для удаления пакета `azdata-cli` воспользуйтесь homebrew.

```bash
brew uninstall azdata-cli
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).