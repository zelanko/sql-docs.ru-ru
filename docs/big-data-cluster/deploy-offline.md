---
title: Развертывание в автономном режиме
titleSuffix: SQL Server big data clusters
description: Узнайте, как выполнить автономное развертывание SQL Server кластера больших данных.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cd8b3128fc11037a5ade494813611d473c995f8f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419365"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Выполнение автономного развертывания SQL Server кластера больших данных

В этой статье описывается, как выполнить автономное развертывание кластера больших данных SQL Server 2019 (Предварительная версия). Кластеры больших данных должны иметь доступ к репозиторию DOCKER, из которого нужно извлечь образы контейнеров. Автономная установка — это одна из тех, где необходимые образы помещаются в частный репозиторий DOCKER. Затем этот частный репозиторий используется в качестве источника образа для нового развертывания.

## <a name="prerequisites"></a>Предварительные требования

- Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Загрузка изображений в частный репозиторий

Ниже описано, как извлечь образы контейнера кластера больших данных из репозитория Майкрософт, а затем отправить их в ваш частный репозиторий.

> [!TIP]
> В следующих шагах описывается процесс. Однако для упрощения задачи можно использовать [автоматизированный сценарий](#automated) вместо выполнения этих команд вручную.

1. Вытяните образы контейнеров больших данных кластера, повторив следующую команду. Замените `<SOURCE_IMAGE_NAME>` на [имя каждого образа](#images). Замените `<SOURCE_DOCKER_TAG>` на тег выпуска кластера больших данных, например **2019-CTP 3.2-Ubuntu**.  

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Войдите в целевой частный реестр DOCKER.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Разметьте локальные образы с помощью следующей команды для каждого образа:

   ```PowerShell
   docker tag mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Отправьте локальные образы в частный репозиторий docker:

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a>Образы контейнеров больших данных кластера

Для автономной установки требуются следующие образы контейнеров кластера больших данных:

 - **MSSQL-AppDeploy-init**
 - **MSSQL-Monitor-флуентбит**
 - **MSSQL-мониторинг-собрано**
 - **MSSQL-Server-данные**
 - **mssql-hadoop**
 - **MSSQL-Monitor-elasticsearch**
 - **MSSQL-Monitor-influxdb**
 - **MSSQL-Security-Knox**
 - **MSSQL-млсервер-r-Runtime**
 - **MSSQL-млсервер-копировать-Runtime**
 - **MSSQL-Controller**
 - **MSSQL-Server-Controller**
 - **MSSQL-Monitor-grafana**
 - **MSSQL-Monitor-kibana**
 - **MSSQL-Service-proxy**
 - **MSSQL-App-Service-proxy**
 - **MSSQL-SSIS-App-Runtime**
 - **MSSQL-Monitor-Telegraf**
 - **MSSQL-млеап-обслуживает-Runtime**
 - **MSSQL-Security-support**

## <a id="automated"></a>Автоматизированный сценарий

Вы можете использовать автоматический сценарий Python, который автоматически запрашивает все необходимые образы контейнеров и передает их в частный репозиторий.

> [!NOTE]
> Python является необходимым условием для использования скрипта. Дополнительные сведения об установке Python см. в [документации по Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Из bash или PowerShell скачайте скрипт с помощью **фигурного скобки**:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Затем выполните сценарий с помощью одной из следующих команд:

   **Windows**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Следуйте инструкциям на экране, чтобы ввести сведения о репозитории Майкрософт и закрытом репозитории. После завершения выполнения сценария все необходимые образы должны находиться в частном репозитории.

## <a name="install-tools-offline"></a>Автономная установка средств

Для развертываний кластера больших данных требуется несколько средств, включая **Python**, **аздата**и **kubectl**. Чтобы установить эти средства на автономном сервере, выполните следующие действия.

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

### <a id="azdata"></a>Установка аздата в автономном режиме

1. На компьютере с доступом к Интернету и [Python](https://wiki.python.org/moin/BeginnersGuide/Download)выполните следующую команду, чтобы скачать все пакеты **аздата** в текущую папку.

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. Скопируйте Скачанные пакеты и файл **требований. txt** на целевой компьютер.

1. Выполните следующую команду на целевом компьютере, указав папку, в которую вы скопировали предыдущие файлы.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a>Установка kubectl в автономном режиме

Чтобы установить **kubectl** на автономный компьютер, выполните следующие действия.

1. Используйте **фигурные скобки** для скачивания **kubectl** в выбранную папку. Дополнительные сведения см. в [статье Установка двоичного файла kubectl с помощью функции «перелистывание](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)».

1. Скопируйте папку на целевой компьютер.

## <a name="deploy-from-private-repository"></a>Развертывание из частного репозитория

Чтобы выполнить развертывание из частного репозитория, выполните действия, описанные в [руководстве по развертыванию](deployment-guidance.md), но используйте пользовательский файл конфигурации развертывания, в котором указаны частные сведения о репозитории DOCKER. Следующие команды **аздата** демонстрируют, как изменить параметры DOCKER в пользовательском файле конфигурации развертывания с именем **Control. JSON**:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

При развертывании появится запрос на ввод имени пользователя и пароля DOCKER, или их можно указать в переменных среды **DOCKER_USERNAME** и **DOCKER_PASSWORD** .

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании кластера больших данных см. в статье [развертывание SQL Server больших кластеров данных в Kubernetes](deployment-guidance.md).
