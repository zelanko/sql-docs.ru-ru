---
title: Развертывание в автономном режиме
titleSuffix: SQL Server big data clusters
description: Сведения о том, как выполнить автономное развертывание кластера больших данных SQL Server.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 243771141bbd255e045ef0a1667235f1c414777b
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155270"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Выполнение автономного развертывания кластера больших данных SQL Server

В этой статье описывается, как выполнить автономное развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Кластеры больших данных должны иметь доступ к репозиторию Docker, из которого извлекаются образы контейнеров. При автономной установке требуемые образы помещаются в частный репозиторий Docker. Затем этот частный репозиторий используется в качестве источника образов для нового развертывания.

## <a name="prerequisites"></a>Предварительные требования

- Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Загрузка образов в частный репозиторий

Ниже описано, как извлечь образы контейнеров кластера больших данных из репозитория Майкрософт, а затем отправить их в ваш частный репозиторий.

> [!TIP]
> Приведенные ниже шаги показывают, как это сделать. Однако для упрощения задачи вместо выполнения этих команд вручную можно использовать [автоматический скрипт](#automated).

1. Извлеките образы контейнеров кластера больших данных, выполняя указанную ниже команду. Замените `<SOURCE_IMAGE_NAME>` на [имя каждого из образов](#images). Замените `<SOURCE_DOCKER_TAG>` на тег выпуска кластера больших данных, например **2019-RC1-Ubuntu**.  

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Войдите в целевой частный реестр Docker.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Пометьте локальные образы, выполнив следующую команду для каждого из них.

   ```PowerShell
   docker tag mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Отправьте локальные образы в частный репозиторий Docker.

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a> Образы контейнеров кластера больших данных

Для автономной установки требуются следующие образы контейнеров кластера больших данных.
- **mssql-app-service-proxy**
- **MSSQL-Control-модуль наблюдения**
- **mssql-controller**
- **MSSQL-DNS**
- **mssql-hadoop**
- **mssql-mleap-serving-runtime**
- **mssql-mlserver-py-runtime**
- **mssql-mlserver-r-runtime**
- **mssql-monitor-collectd**
- **mssql-monitor-elasticsearch**
- **mssql-monitor-fluentbit**
- **mssql-monitor-grafana**
- **mssql-monitor-influxdb**
- **mssql-monitor-kibana**
- **mssql-monitor-telegraf**
- **MSSQL-Security-домаинктл**
- **mssql-security-knox**
- **mssql-security-support**
- **mssql-server**
- **mssql-server-controller**
- **mssql-server-data**
- **MSSQL-Server-Ha**
- **mssql-service-proxy**
- **mssql-ssis-app-runtime**


## <a id="automated"></a> Автоматический скрипт

Вы можете использовать автоматический скрипт Python, который автоматически извлекает все необходимые образы контейнеров и передает их в частный репозиторий.

> [!NOTE]
> Обязательным условием для использования этого скрипта является наличие Python. Дополнительные сведения об установке Python см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Скачайте скрипт из Bash или PowerShell с помощью **curl**.

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Затем выполните скрипт с помощью одной из следующих команд.

   **Windows:**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux:**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Следуйте инструкциям на экране, чтобы ввести сведения о репозитории Майкрософт и частном репозитории. После завершения выполнения скрипта все необходимые образы должны находиться в частном репозитории.

## <a name="install-tools-offline"></a>Автономная установка средств

Для развертываний кластера больших данных требуется несколько средств, включая `azdata`Python, и **kubectl**. Чтобы установить эти средства на автономном сервере, выполните указанные ниже действия.

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

### <a id="azdata"></a> Автономная установка azdata

1. На компьютере с доступом к Интернету и [Python](https://wiki.python.org/moin/BeginnersGuide/Download)выполните следующую команду, чтобы скачать все `azdata` пакеты в текущую папку.

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. Скопируйте загруженные пакеты и `requirements.txt` файл на целевой компьютер.

1. Выполните указанную ниже команду на целевом компьютере, указав папку, куда вы скопировали предыдущие файлы.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a> Автономная установка kubectl

Чтобы установить **kubectl** на автономный компьютер, выполните указанные ниже действия.

1. Используйте **curl**, чтобы скачать **kubectl** в выбранную вами папку. Дополнительные сведения см. в разделе [Установка двоичного файла kubectl с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl).

1. Скопируйте эту папку на целевой компьютер.

## <a name="deploy-from-private-repository"></a>Развертывание из частного репозитория

Для развертывания из частного репозитория выполните действия, описанные в [руководстве по развертыванию](deployment-guidance.md), но используйте пользовательский файл конфигурации развертывания, в котором указаны сведения о вашем частном репозитории Docker. Следующие `azdata` команды демонстрируют, как изменить параметры DOCKER в файле конфигурации пользовательского развертывания с именем `control.json`:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

При развертывании появится запрос на ввод имени пользователя и пароля DOCKER, либо можно указать их в `DOCKER_USERNAME` переменных среды и. `DOCKER_PASSWORD`

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании кластера больших данных см. в разделе [развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md).
