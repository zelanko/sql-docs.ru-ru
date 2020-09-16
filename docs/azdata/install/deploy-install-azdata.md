---
title: Установка azdata
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство azdata для установки кластеров больших данных и управления ими.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 408dec76480a36ff2280926147b948859fa7088d
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89734099"
---
# <a name="install-azdata"></a>установить `azdata`;

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Служебная программа командной строки `azdata` написана на языке Python для начальной загрузки кластера больших данных и управления им через REST API. 

## <a name="find-latest-version"></a>Выбор последней версии

Список файлов для последней версии всегда доступен по адресу [https://aka.ms/azdata](https://aka.ms/azdata).

Чтобы узнать, какая версия установлена и нужно ли ее обновить, выполните команду `azdata --version`.

## <a name="os-specific-instructions"></a>Инструкции для конкретных ОС

* [Установка в Windows](../install/deploy-install-azdata-installer.md)
* [Установка в macOS](../install/deploy-install-azdata-macos.md)
* Установка в Linux или [подсистеме Windows для Linux (WSL)](/windows/wsl/about/)
   * [Установка с помощью apt в Debian и Ubuntu](../install/deploy-install-azdata-linux-package.md)
   * [Установка с помощью yum в RHEL или CentOS](../install/deploy-install-azdata-yum.md)
   * [Установка с помощью Zypper в openSUSE или SLE](../install/deploy-install-azdata-zypper.md)
   * [установка из скрипта](../install/deploy-install-azdata-pip.md).

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).
