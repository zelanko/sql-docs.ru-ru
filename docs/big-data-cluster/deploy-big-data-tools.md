---
title: Установка инструментов для больших данных
titleSuffix: SQL Server big data clusters
description: Узнайте, как устанавливать средства, используемые [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] с (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f30b3b2e3c8503d2ac74ede8c1a45114a6b1d555
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653400"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Установка средств для работы с большими данными SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются клиентские средства, которые должны быть установлены для создания, управления и [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] использования (Предварительная версия). В следующем разделе приведен список средств и ссылки на инструкции по установке. Перед развертыванием кластера больших данных настройте средства, отмеченные как обязательные в Windows или Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Средства кластеров больших данных

В следующей таблице перечислены общие инструменты кластера больших данных и способы их установки.

| Tool | Обязательно | Описание | Установка |
|---|---|---|---|
| **python** | Да | Python — это интерпретируемый объектно-ориентированный высокоуровневый язык программирования с динамической семантикой. Многие части кластеров больших данных для SQL Server используют Python. | [Установка Python](#python)|
| **azdata** | Да | Программа командной строки для установки кластера больших данных и управления им. | [Установка](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | Да | Программа командной строки для мониторинга базового кластера Kubernetes ([дополнительные сведения](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (версия для инсайдеров)** | Да | Кроссплатформенный графический инструмент для запроса SQL Server ([дополнительные сведения](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Установка](https://aka.ms/azdata-insiders) |
| **Расширение SQL Server 2019** | Да | Расширение для Azure Data Studio, которое поддерживает подключение к кластеру больших данных. Также включает мастер виртуализации данных. | [Установка](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Для AKS | Современный интерфейс командной строки для управления службами Azure. Используется с развертываниями кластера больших данных AKS ([дополнительные сведения](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Установка](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Необязательно | Современный интерфейс командной строки для запроса SQL Server ([дополнительные сведения](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Для некоторых сценариев | Старый интерфейс командной строки для запроса SQL Server ([дополнительные сведения](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Для некоторых сценариев | Программа командной строки для передачи данных по URL-адресам. | [Windows](https://curl.haxx.se/windows/) \| Linux: установка пакета curl |

<sup>1</sup> Необходимо использовать kubectl версии 1.10 или более поздней. Кроме того, версия kubectl должна отстоять от младшей версии кластера Kubernetes не более чем на единицу. Если вы хотите установить определенную версию клиента kubectl, см. статью [Установка двоичных файлов kubectl при помощи curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (в Windows 10 используйте cmd.exe, а не Windows PowerShell для запуска curl). 

> [!TIP]
> Чтобы использовать kubectl с ранее развернутым кластером в службе Azure Kubernetes (AKS), необходимо задать контекст кластера с помощью следующей команды Azure CLI:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Необходимо использовать Azure CLI версии 2.0.4 или более поздней. При необходимости выполните команду `az --version`, чтобы определить версию.

<sup>3</sup> Если вы используете Windows 10, то **curl** уже есть в PATH при запуске из командной строки cmd. Для других версий Windows скачайте **curl** по ссылке и добавьте в PATH.

## <a name="which-tools-are-required"></a>Какие средства требуются?

В предыдущей таблице представлены все общие средства, используемые с кластерами больших данных. Необходимые инструменты зависят от вашего сценария. Но в целом следующие средства наиболее важны для управления, подключения к кластеру и запросов к нему.

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **Расширение SQL Server 2019**

Остальные инструменты требуются только в отдельных сценариях. **Azure CLI** можно использовать для управления службами Azure, связанными с развертываниями AKS. **mssql-cli** — это необязательное, но полезное средство, которое позволяет подключаться к главному экземпляру SQL Server в кластере и запускать запросы из командной строки. Если вы планируете установить демонстрационные данные с помощью скрипта GitHub, то вам потребуются **sqlcmd** и **curl**.

### <a id="python"></a> Автономная установка Python

1. На компьютере с доступом в Интернет скачайте один из следующих сжатых файлов с Python.

   | Операционная система | Загрузить |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Скопируйте сжатый файл на целевой компьютер и извлеките его в выбранную папку.

1. Только для Windows: запустите `installLocalPythonPackages.bat` из этой папки и передайте полный путь к ней в виде параметра.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="next-steps"></a>Следующие шаги

После настройки всех средств разверните кластер больших данных SQL Server 2019 в Kubernetes в облаке или в локальной среде. Дополнительные сведения см. в следующих статьях по развертыванию:

- [Краткое руководство. Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
- [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] на Kubernetes](deployment-guidance.md)

Дополнительные сведения о кластерах больших данных см. в разделе [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]что такое?](big-data-cluster-overview.md).
