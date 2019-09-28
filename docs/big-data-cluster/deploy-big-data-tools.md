---
title: Установка инструментов для больших данных
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средства, используемые с [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cbb34d5cd209281a5c97d819c7741503d234ad2d
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342021"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Установка средств для работы с большими данными SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются клиентские средства, которые должны быть установлены для создания, управления и использования [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Предварительная версия). В следующем разделе приведен список средств и ссылки на инструкции по установке. Перед развертыванием кластера больших данных настройте средства, отмеченные как обязательные в Windows или Linux.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Средства кластеров больших данных

В следующей таблице перечислены общие инструменты кластера больших данных и способы их установки.

| Инструмент | Обязательно | Описание | Установка |
|---|---|---|---|
| **python** | Да | Python — это интерпретируемый объектно-ориентированный высокоуровневый язык программирования с динамической семантикой. Многие части кластеров больших данных для SQL Server используют Python. | [Установка Python](#python)|
| **azdata** | Да | Программа командной строки для установки кластера больших данных и управления им. | [Установка](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | Да | Программа командной строки для мониторинга базового кластера Kubernetes ([дополнительные сведения](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-using-native-package-management) |
| **Версия-кандидат Azure Data Studio SQL Server 2019 (RC)** | Да | Кросс-платформенный графический инструмент для запроса SQL Server. | [Установка](#download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc) |
| **Расширение SQL Server 2019** | Да | Расширение для Azure Data Studio, которое поддерживает подключение к кластеру больших данных. Также включает мастер виртуализации данных. | [Установка](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Для AKS | Современный интерфейс командной строки для управления службами Azure. Используется с развертываниями кластера больших данных AKS ([дополнительные сведения](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Установка](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Необязательно | Современный интерфейс командной строки для запроса SQL Server ([дополнительные сведения](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Для некоторых сценариев | Старый интерфейс командной строки для запроса SQL Server ([дополнительные сведения](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Для некоторых сценариев | Программа командной строки для передачи данных по URL-адресам. | [Windows](https://curl.haxx.se/windows/) \| Linux: установка пакета curl |

<sup>1</sup> необходимо использовать kubectl версии 1,13 или более поздней. Кроме того, версия kubectl должна отстоять от младшей версии кластера Kubernetes не более чем на единицу. Если вы хотите установить определенную версию клиента kubectl, см. статью [Установка двоичных файлов kubectl при помощи curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (в Windows 10 используйте cmd.exe, а не Windows PowerShell для запуска curl).

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

## <a name="download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc"></a>Загрузите и установите Azure Data Studio SQL Server 2019 версии-кандидата (RC)

Azure Data Studio SQL Server 2019 RC предоставляет возможности и функции, специально предназначенные для SQL Server 2019 RC.

Для обычных рабочих выпусков Azure Data Studio следуйте инструкциям в статье [Загрузка и установка Azure Data Studio](../azure-data-studio/download.md).

|Платформа|Загрузить|Дата выпуска| Версия |
|:---|:---|:---|:---|
|Windows|[Пользовательский установщик (рекомендуется)](https://go.microsoft.com/fwlink/?linkid=2102435)<br>[Системный установщик](https://go.microsoft.com/fwlink/?linkid=2102523)<br>[ZIP](https://go.microsoft.com/fwlink/?linkid=2102524)|27 августа 2019 г. |RC 1.11.0 — предварительные оценки|
|macOS|[ZIP](https://go.microsoft.com/fwlink/?linkid=2102436)|27 августа 2019 г. |RC 1.11.0 — предварительные оценки|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2102526)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2102437)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2102525)|27 августа 2019 г. |RC 1.11.0 — предварительные оценки|

Подробнее см. в [заметках о выпуске](../big-data-cluster/release-notes-big-data-cluster.md).

### <a name="get-azure-data-studio-for-windows"></a>Получение Azure Data Studio для Windows

Этот выпуск [!INCLUDE[name-sos](../includes/name-sos-short.md)] включает стандартные средства установщика Windows и ZIP-файл.

Рекомендуется использовать *пользовательский установщик*, так как он не требует прав администратора, что упрощает установку и обновление. Он не требует прав администратора, так как расположение находится в пользовательской локальной папке AppData (LOCALAPPDATA). Пользовательский установщик также обеспечивает более гладкую фоновую работу по обновлению. Дополнительные сведения см. в статье [Пользовательская настройка в Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Пользовательский установщик** (рекомендуется)

1. Скачайте и запустите [*пользовательский* установщик [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Windows](https://go.microsoft.com/fwlink/?linkid=2102435).
2. Запустите приложение [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].

**Системный установщик**

1. Скачайте и запустите [*пользовательский* установщик [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Windows](https://go.microsoft.com/fwlink/?linkid=2102523).
2. Запустите приложение [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].

**ZIP-файл**

1. Скачайте [ZIP-файл [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Windows](https://go.microsoft.com/fwlink/?linkid=2102524).
2. Перейдите к скачанному файлу и извлеките его содержимое.
3. Выполнить `\azuredatastudio-windows\azuredatastudio.exe`

### <a name="get-azure-data-studio-for-macos"></a>Получение Azure Data Studio для macOS

1. Скачайте [[!INCLUDE[name-sos](../includes/name-sos-short.md)] для macOS](https://go.microsoft.com/fwlink/?linkid=2102436).
2. Чтобы извлечь содержимое ZIP-файла, дважды щелкните его.
3. Чтобы сделать [!INCLUDE[name-sos](../includes/name-sos-short.md)] доступным на *панели запуска*, перетащите *Azure Data Studio.app* в папку *Приложения*.

### <a name="get-azure-data-studio-for-linux"></a>Получение Azure Data Studio для Linux

1. Скачайте [!INCLUDE[name-sos](../includes/name-sos-short.md)] для Linux с помощью одного из установщиков или архива tar.gz:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2102526)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2102437)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2102525)
1. Чтобы извлечь файл и запустить [!INCLUDE[name-sos](../includes/name-sos-short.md)], откройте новое окно терминала и введите следующие команды:

   **Установка в Debian:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **Установка из RPM:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **Установка из tar.gz:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > В Debian, Redhat и Ubuntu, возможно, будут отсутствовать некоторые зависимости. Чтобы установить эти зависимости с учетом вашей версии Linux, используйте следующие команды:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```

### <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Программа [!INCLUDE[name-sos](../includes/name-sos-short.md)] работает в Windows, macOS и Linux, а также поддерживается на следующих платформах:

#### <a name="windows"></a>Windows

- Windows 10 (64-разрядная)
- Windows 8.1 (64-разрядная)
- Windows 8 (64-разрядная)
- Windows 7 с пакетом обновления 1 (SP1) (64-разрядная) — требуется [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

#### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

#### <a name="linux"></a>Linux

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 с пакетом обновления 2 (SP2)
- Ubuntu 16.04

## <a name="next-steps"></a>Следующие шаги

После настройки всех средств разверните кластер больших данных SQL Server 2019 в Kubernetes в облаке или в локальной среде. Дополнительные сведения см. в следующих статьях по развертыванию:

- [Краткое руководство. Развертывание кластера больших данных SQL Server в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
- [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] на Kubernetes](deployment-guidance.md)

Дополнительные сведения о кластерах больших данных см. в разделе [что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
