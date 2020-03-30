---
title: Установка инструментов для больших данных
titleSuffix: SQL Server big data clusters
description: Узнайте, как устанавливать средства, используемые с [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 12dea4163feba35af6346d347503f42ab31c852a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "77173625"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Установка средств для работы с большими данными SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются клиентские средства, которые должны быть установлены для создания, контроля и использования [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. В следующем разделе приведен список средств и ссылки на инструкции по установке. Перед развертыванием кластера больших данных настройте средства, отмеченные как обязательные в Windows или Linux.

## <a name="big-data-cluster-tools"></a>Средства кластеров больших данных

В следующей таблице перечислены общие инструменты кластера больших данных и способы их установки.

| Инструмент | Обязательно | Описание | Установка |
|---|---|---|---|
| `python` | Да | Python — это интерпретируемый объектно-ориентированный высокоуровневый язык программирования с динамической семантикой. Многие части кластеров больших данных для SQL Server используют Python. | [Установка Python](#python)|
| `azdata` | Да | Программа командной строки для установки кластера больших данных и управления им. | [Установка](deploy-install-azdata.md) |
| `kubectl`<sup>1</sup> | Да | Программа командной строки для мониторинга базового кластера Kubernetes ([дополнительные сведения](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-using-native-package-management) |
| **Azure Data Studio** | Да | Кроссплатформенный графический инструмент для запроса SQL Server. | [Установка](https://aka.ms/getazuredatastudio) |
| **Расширение Data Virtualization** | Да | Расширение для Azure Data Studio, предоставляющее мастер виртуализации данных. | [Установка](../azure-data-studio/data-virtualization-extension.md) |
| **Azure CLI**<sup>2</sup> | Для AKS | Современный интерфейс командной строки для управления службами Azure. Используется с развертываниями кластера больших данных AKS ([дополнительные сведения](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Установка](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Необязательно | Современный интерфейс командной строки для запроса SQL Server ([дополнительные сведения](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Для некоторых сценариев | Старый интерфейс командной строки для запроса SQL Server ([дополнительные сведения](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). Перед установкой пакета SQLCMD может потребоваться установка драйвера Microsoft ODBC 11 для SQL Server. | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| `curl`<sup>3</sup> | Для некоторых сценариев | Программа командной строки для передачи данных по URL-адресам. | [Windows](https://curl.haxx.se/windows/) \| Linux: установите пакет cURL |

<sup>1</sup> Необходимо использовать `kubectl` версии 1.13 или более поздней. Кроме того, версия `kubectl` должна отстоять от младшей версии кластера Kubernetes не более чем на единицу. Если вы хотите установить определенную версию в клиенте `kubectl`, см. статью [Установка двоичных файлов `kubectl` при помощи curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (в Windows 10 для запуска curl используйте cmd.exe, а не Windows PowerShell).

> [!TIP]
> Чтобы использовать `kubectl` с ранее развернутым кластером в службе Azure Kubernetes (AKS), необходимо задать контекст кластера с помощью следующей команды Azure CLI:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Необходимо использовать Azure CLI версии 2.0.4 или более поздней. При необходимости выполните команду `az --version`, чтобы определить версию.

<sup>3</sup> Если вы используете Windows 10, то `curl` уже указан в каталоге PATH при запуске из командной строки cmd. Если используются другие версии Windows, скачайте `curl` по ссылке и поместите его в каталоге PATH.

## <a name="which-tools-are-required"></a>Какие средства требуются?

В предыдущей таблице представлены все общие средства, используемые с кластерами больших данных. Необходимые инструменты зависят от вашего сценария. Но в целом следующие средства наиболее важны для управления, подключения к кластеру и запросов к нему.

- `azdata`
- `kubectl`
- **Azure Data Studio**
- **Расширение Data Virtualization**

Остальные инструменты требуются только в отдельных сценариях. **Azure CLI** можно использовать для управления службами Azure, связанными с развертываниями AKS. **mssql-cli** — это необязательное, но полезное средство, которое позволяет подключаться к главному экземпляру SQL Server в кластере и запускать запросы из командной строки. Если вы планируете установить демонстрационные данные с помощью скрипта GitHub, вам потребуются **sqlcmd** и `curl`.

### <a name="install-python-offline"></a><a id="python"></a> Автономная установка Python

1. На компьютере с доступом в Интернет скачайте один из следующих сжатых файлов с Python.

   | Операционная система | Скачивание |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Скопируйте сжатый файл на целевой компьютер и извлеките его в выбранную папку.

1. Только для Windows: запустите `installLocalPythonPackages.bat` из этой папки и передайте полный путь к ней в виде параметра.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="download-and-install-azure-data-studio"></a>Скачивание и установка Azure Data Studio

Azure Data Studio предоставляет функциональные возможности и компоненты специально для работы с кластерами больших данных SQL Server.

[Получите последнюю версию Azure Data Studio](https://aka.ms/getazuredatastudio).

Подробнее см. в [заметках о выпуске](../big-data-cluster/release-notes-big-data-cluster.md).

## <a name="next-steps"></a>Дальнейшие действия

После настройки всех средств разверните кластер больших данных SQL Server 2019 в Kubernetes в облаке или в локальной среде. Дополнительные сведения см. в следующих статьях по развертыванию:

- [Краткое руководство. Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
- [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md)

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
