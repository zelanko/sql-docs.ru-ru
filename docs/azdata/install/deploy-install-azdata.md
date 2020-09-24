---
title: Установка azdata
titleSuffix: ''
description: Сведения об установке средства azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 7939aa1575aaeec8edff33a9a9f7101a1014abc2
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914926"
---
# <a name="install-azdata"></a>установить `azdata`;

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/azdata.md)]

Служебная программа командной строки `azdata`, написанная на языке Python, предназначена для начальной загрузки и контроля служб данных с помощью интерфейсов REST API. 

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

Используйте azdata с Кластерами больших данных: [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Используйте azdata со [службами данных с поддержкой Azure Arc](/azure/azure-arc/data/)
