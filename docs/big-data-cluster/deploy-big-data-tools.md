---
title: Установка инструментов для больших данных
titleSuffix: SQL Server 2019 big data clusters
description: Сведения об установке средств, используемых с кластерами SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 54ea67e8b85d4e9a1a8cdbe4b40cf1bb9c3f1062
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241605"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Установка средств SQL Server 2019 больших данных

В этой статье описываются клиентские средства, которые должны быть установлены для создания, управления, и больших данных с помощью SQL Server 2019 кластеров (Предварительная версия).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Средства кластера больших данных

В следующей таблице перечислены общие средства кластера больших данных и способах их установки:

| Инструмент | Обязательно | Описание | Установка |
|---|---|---|---|
| **mssqlctl** | Да | Средство командной строки для установки и управления ими кластерам больших данных. | [Установка](deploy-install-mssqlctl.md) |
| **kubectl**<sup>1</sup> | Да | Средство командной строки для мониторинга базового кластера Kuberentes ([сведения](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio** | Да | Кросс платформенных графическое средство для выполнения запросов к SQL Server ([сведения](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Установка](../azure-data-studio/download.md) |
| **Расширение SQL Server 2019** | Да | Расширение для Azure Data Studio, которая поддерживает подключение к кластеру больших данных. Также предоставляет мастер виртуализации данных. | [Установка](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Для AKS | Современный интерфейс командной строки для управления службами Azure. Используется при развертывании кластера AKS больших данных ([сведения](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Установка](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Необязательно | Современный интерфейс командной строки для выполнения запросов к SQL Server ([сведения](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Для некоторых сценариев | Устаревшие средства командной строки для выполнения запросов к SQL Server ([сведения](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Для некоторых сценариев | Программа командной строки для передачи данных с URL-адреса. | [Windows](https://curl.haxx.se/windows/) \| Linux: пакет установки curl |

<sup>1</sup> необходимо использовать версию kubectl 1,10 или более поздней версии. Кроме того версия Kubectl должна быть, плюс или минус один дополнительный номер версии кластера Kubernetes. Если вы хотите установить конкретную версию на клиент kubectl, см. в разделе [установки kubectl двоичных с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (на Windows 10 с помощью cmd.exe и не Windows PowerShell для выполнения curl).

<sup>2</sup> необходимо использовать Azure CLI версии 2.0.4 или более поздней версии. Запустите `az --version` чтобы узнать версию, при необходимости.

<sup>3</sup> при запуске в Windows 10, **curl** уже указан в пути, при запуске из командной строки. Для других версий Windows, скачайте **curl** по ссылке и поместите его в свой путь.

## <a name="which-tools-are-required"></a>Какие инструменты требуются?

В предыдущей таблице приводятся все распространенных средств, которые используются с кластерами больших данных. Какие инструменты требуются зависит от сценария. Но в общем случае следующие средства наиболее важны для управления, запросы и подключение к кластеру:

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **Расширение SQL Server 2019**

Другие средства необходимы только в определенных сценариях. **Azure CLI** можно использовать для управления службами Azure, связанные с развертыванием AKS. **MSSQL-cli** — это необязательно, но полезные средство, которое позволяет подключиться к основной экземпляр SQL Server в кластере и выполнения запросов из командной строки. И **sqlcmd** и **curl** необходимы, если вы планируете установить образец данных с помощью сценария GitHub.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
