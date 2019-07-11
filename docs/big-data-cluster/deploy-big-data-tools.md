---
title: Установка инструментов для больших данных
titleSuffix: SQL Server big data clusters
description: Сведения об установке средств, используемых с кластерами SQL Server 2019 больших данных (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1862c6c16aaecca7888f00cb6ca5deeb7138ea03
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728978"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Установка средств SQL Server 2019 больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются клиентские средства, которые должны быть установлены для создания, управления, и больших данных с помощью SQL Server 2019 кластеров (Предварительная версия). Следующий раздел содержит список инструментов и ссылки на инструкции по установке. Перед развертыванием кластера больших данных, настройте средства, необходимые на Windows или Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Средства кластера больших данных

В следующей таблице перечислены общие средства кластера больших данных и способах их установки:

| Инструмент | Обязательно | Описание | Установка |
|---|---|---|---|
| **mssqlctl** | Да | Средство командной строки для установки и управления ими кластерам больших данных. | [Установка](deploy-install-mssqlctl.md) |
| **kubectl**<sup>1</sup> | Да | Средство командной строки для мониторинга базового кластера Kuberentes ([сведения](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (участников программы предварительной оценки)** | Да | Кросс платформенных графическое средство для выполнения запросов к SQL Server ([сведения](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Установка](https://aka.ms/azdata-insiders) |
| **Расширение SQL Server 2019** | Да | Расширение для Azure Data Studio, которая поддерживает подключение к кластеру больших данных. Также предоставляет мастер виртуализации данных. | [Установка](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Для AKS | Современный интерфейс командной строки для управления службами Azure. Используется при развертывании кластера AKS больших данных ([сведения](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Установка](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Необязательно | Современный интерфейс командной строки для выполнения запросов к SQL Server ([сведения](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Для некоторых сценариев | Устаревшие средства командной строки для выполнения запросов к SQL Server ([сведения](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Для некоторых сценариев | Программа командной строки для передачи данных с URL-адреса. | [Windows](https://curl.haxx.se/windows/) \| Linux: пакет установки curl |

<sup>1</sup> необходимо использовать версию kubectl 1,10 или более поздней версии. Кроме того версия kubectl должна быть, плюс или минус один дополнительный номер версии кластера Kubernetes. Если вы хотите установить конкретную версию на клиент kubectl, см. в разделе [установки kubectl двоичных с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (на Windows 10 с помощью cmd.exe и не Windows PowerShell для выполнения curl). 

> [!TIP]
> Чтобы использовать kubectl с ранее развернутого кластера в службе Azure Kubernetes (AKS), необходимо задать контекст кластера с помощью следующей команды Azure CLI:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

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

После настройки средства, развертывание кластера SQL Server 2019 больших данных в Kubernetes в облаке или локальной. Дополнительные сведения см. в следующих статьях развертывания:

- [Краткое руководство. Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
- [Развертывание кластеров больших данных SQL Server в Kubernetes](deployment-guidance.md)

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
