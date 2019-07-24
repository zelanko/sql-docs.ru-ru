---
title: Установка инструментов для больших данных
titleSuffix: SQL Server big data clusters
description: Узнайте, как устанавливать средства, используемые с кластерами больших данных SQL Server 2019 (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 757209ff89fd40dcc737b65d3b19f2a7d4ef247b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419456"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Установка средств для обработки больших данных SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются клиентские средства, которые должны быть установлены для создания, управления и использования кластеров больших данных SQL Server 2019 (Предварительная версия). В следующем разделе приведен список средств и ссылки на инструкции по установке. Перед развертыванием кластера больших данных настройте средства, отмеченные как обязательные в Windows или Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Инструменты кластера больших данных

В следующей таблице перечислены общие инструменты кластера больших данных и способы их установки.

| Инструмент | Обязательно | Описание | Установка |
|---|---|---|---|
| **языке** | Да | Python — это интерпретируемый, объектно-ориентированный и высокоуровневый язык программирования с динамической семантикой. Многие части кластеров больших данных для SQL Server используют Python. | [Установка Python](#python)|
| **аздата** | Да | Программа командной строки для установки кластера больших данных и управления им. | [Установка](deploy-install-azdata.md) |
| **kubectl** <sup>1</sup> | Да | Программа командной строки для мониторинга базового кластера Куберентес ([Дополнительные сведения](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (предварительные оценки)** | Да | Кросс-платформенный графический инструмент для запроса SQL Server ([Дополнительные сведения](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Установка](https://aka.ms/azdata-insiders) |
| **Расширение SQL Server 2019** | Да | Расширение для Azure Data Studio, которое поддерживает подключение к кластеру больших данных. Также предоставляет мастер виртуализации данных. | [Установка](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI** <sup>2</sup> | Для AKS | Современный интерфейс командной строки для управления службами Azure. Используется с развертываниями кластера больших данных AKS ([Дополнительные сведения](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Установка](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Необязательно | Современный интерфейс командной строки для запроса SQL Server ([Дополнительные сведения](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Для некоторых сценариев | Устаревшая программа командной строки для запроса SQL Server ([Дополнительные сведения](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **перелистывание** <sup>3</sup> | Для некоторых сценариев | Программа командной строки для передачи данных с URL-адресами. | [Windows](https://curl.haxx.se/windows/) \| Linux: Установка парного пакета |

<sup>1</sup> необходимо использовать kubectl версии 1,10 или более поздней. Кроме того, версия kubectl должна быть плюс или минус одна младшая версия кластера Kubernetes. Если вы хотите установить определенную версию на клиенте kubectl, см. статью [Установка двоичных файлов kubectl через фигурные скобки](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (в Windows 10), используйте Cmd. exe, а не Windows PowerShell, чтобы выполнить прилистывание. 

> [!TIP]
> Чтобы использовать kubectl с ранее развернутым кластером в службе Kubernetes Azure (AKS), необходимо задать контекст кластера с помощью следующей Azure CLI команды:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> необходимо использовать Azure CLI версии 2.0.4 или более поздней. При `az --version` необходимости выполните команду, чтобы найти версию.

<sup>3</sup> если вы используете в Windows **10, то** при запуске из командной строки в качестве приводятся такие же пути. Для других версий Windows Загрузите фигурные **скобки** с помощью ссылки и поместите ее в свой путь.

## <a name="which-tools-are-required"></a>Какие средства требуются?

В предыдущей таблице представлены все общие средства, используемые с кластерами больших данных. Необходимые инструменты зависят от вашего сценария. Но в целом следующие средства наиболее важны для управления, подключения к кластеру и выполнения запросов к нему.

- **аздата**
- **kubectl**
- **Azure Data Studio**
- **Расширение SQL Server 2019**

Остальные инструменты требуются только в определенных сценариях. **Azure CLI** можно использовать для управления службами Azure, связанными с развертываниями AKS. **MSSQL-CLI** — это необязательное, но полезное средство, которое позволяет подключаться к экземпляру SQL Server master в кластере и запускать запросы из командной строки. Если вы планируете установить демонстрационные данные с помощью скрипта GitHub, то программа **sqlcmd** и **фигурная скобка** обязательна.

### <a id="python"></a>Установка Python в автономном режиме

1. На компьютере с доступом к Интернету Скачайте один из следующих сжатых файлов, содержащих Python:

   | Операционная система | Загрузить |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Скопируйте сжатый файл на целевой компьютер и извлеките его в выбранную папку.

1. Только для Windows, запустите `installLocalPythonPackages.bat` из этой папки и передайте полный путь к той же папке, что и параметр.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="next-steps"></a>Следующие шаги

После настройки средств разверните кластер больших данных SQL Server 2019 в Kubernetes в облаке или в локальной среде. Дополнительные сведения см. в следующих статьях по развертыванию:

- [QuickStart Развертывание SQL Server кластера больших данных в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
- [Развертывание SQL Server кластеров больших данных в Kubernetes](deployment-guidance.md)

Дополнительные сведения о кластерах больших данных см. в статье [что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md).
