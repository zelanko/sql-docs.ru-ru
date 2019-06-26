---
title: Автономное развертывание
titleSuffix: SQL Server big data clusters
description: Узнайте, как выполнение автономного развертывания кластера больших данных SQL Server.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0f3bfcfba0cfb972c7d02042bc98aa461eb110bb
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388807"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Выполнение автономного развертывания кластера больших данных SQL Server

В этой статье описывается выполнение автономного развертывания кластера SQL Server 2019 больших данных (Предварительная версия). Кластерами больших данных необходим доступ к репозиторию Docker из которого для образов контейнеров по запросу. Автономной установки является одним где необходимые изображения, помещаются в частный репозиторий Docker. Этот частный репозиторий затем используется как источник изображения для нового развертывания.

## <a name="prerequisites"></a>предварительные требования

- Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Загрузка изображений в частный репозиторий

Следующие шаги описывают, как извлекать образы контейнера кластера больших данных из репозитория Microsoft и затем передать их в вашем личном репозитории.

> [!TIP]
> На следующих шагах описывается процесс. Тем не менее, чтобы упростить задачу, можно использовать [автоматизированный скрипт](#automated) вместо вручную, выполнив следующие команды.

1. Сначала войдите в реестр Microsoft Docker **docker login** команды. Используйте имя пользователя и пароль, предоставленные вам в рамках программы раннего внедрения Microsoft.

   ```PowerShell
   docker login private-repo.microsoft.com -u  <SOURCE_DOCKER_USERNAME> -p <SOURCE_DOCKER_PASSWORD>
   ```

   > [!TIP]
   > Эти команды используют PowerShell в качестве примера, но их можно запускать из командной строки, bash или любой командной оболочки, который можно запустить docker. В Linux, добавление `sudo` для каждой команды.

1. Получайте образы контейнеров кластера больших данных, повторив следующую команду. Замените `<SOURCE_IMAGE_NAME>` с каждым [имя образа](#images). Замените `<SOURCE_DOCKER_TAG>` с тегом для больших объемов данных кластера выпуска, такие как **ctp3.1**.  

   ```PowerShell
   docker pull private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Войдите на целевой частного реестра Docker.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Тег локальным образам, выполнив следующую команду для каждого образа:

   ```PowerShell
   docker tag private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Отправьте локальных образов в частный репозиторий Docker:

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a> Образы контейнеров кластера больших данных

Для автономной установки необходимы следующие образы контейнера кластера больших данных:

 - **MSSQL-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **MSSQL-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-java**
 - **mssql-mlservices-pythonserver**
 - **mssql-mlservices-rserver**
 - **MSSQL-monitor-elasticsearch**
 - **MSSQL-monitor-influxdb**
 - **mssql-security-knox**
 - **mssql-mlserver-r-runtime**
 - **MSSQL-mlserver-py-runtime**
 - **mssql-controller**
 - **mssql-server-controller**
 - **MSSQL-monitor-grafana**
 - **MSSQL-monitor-kibana**
 - **mssql-service-proxy**
 - **mssql-app-service-proxy**
 - **mssql-ssis-app-runtime**
 - **MSSQL-monitor-telegraf**
 - **MSSQL-mleap обслуживания runtime**
  

## <a id="automated"></a> Автоматизированного скрипта

Можно использовать скрипт автоматической python, который будет автоматически извлекать все образы необходимый контейнер и отправить его в частный репозиторий.

> [!NOTE]
> Python является необходимым условием для работы с помощью скрипта. Дополнительные сведения о том, как установить Python см. в разделе [документации Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Из bash или PowerShell, скачайте скрипт с **curl**:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Затем запустите сценарий с одной из следующих команд:

   **Windows:**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux:**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Следуйте инструкциям на экране для ввода репозиторий Майкрософт и данные частный репозиторий. По завершении выполнения скрипта все необходимые изображения должен находиться в вашем личном репозитории.

## <a name="install-tools-offline"></a>Установка средств в автономном режиме

Развертывания кластера больших данных требуют несколько средств, включая **Python**, **mssqlctl**, и **kubectl**. Следуйте инструкциям ниже для установки этих средств на сервере вне сети.

### <a id="python"></a> Установка python в автономном режиме

1. На компьютере с доступом к Интернету Загрузите один из следующих сжатые файлы, содержащие Python:

   | Операционная система | Загрузить |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Скопируйте сжатый файл на целевой компьютер и извлеките его содержимое в папку по своему усмотрению.

1. Для Windows, запустите `installLocalPythonPackages.bat` из этой папки и передайте полный путь к той же папке, что параметр.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a id="mssqlctl"></a> Установка mssqlctl в автономном режиме

1. На компьютере с доступом к Интернету и [Python](https://wiki.python.org/moin/BeginnersGuide/Download), выполните следующую команду, чтобы загрузить все **mssqlctl** пакетов в текущую папку.

   ```PowerShell
   pip download -r https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. Скачайте **requirements.txt** файла.

   ```PowerShell
   curl -o requirements.txt "https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt"
   ```

1. Скопируйте скачанные пакеты и **requirements.txt** файл на целевой компьютер.

1. Выполните следующую команду на целевом компьютере, указав папку, в который вы скопировали предыдущие файлы в.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a> Установка kubectl в автономном режиме

Чтобы установить **kubectl** на автономном компьютере, выполните следующие действия.

1. Используйте **curl** для загрузки **kubectl** в папку по своему усмотрению. Дополнительные сведения см. в разделе [установите kubectl двоичного файла с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl).

1. Скопируйте папку на целевом компьютере.

## <a name="deploy-from-private-repository"></a>Развертывание из закрытого репозитория

Чтобы развернуть из закрытого репозитория, выполните действия, описанные в [руководство по развертыванию](deployment-guidance.md), но использовать файл конфигурации развертывания, который указывает личных сведений репозитория Docker. Следующие **mssqlctl** командах показано, как изменение параметров Docker в файле конфигурации развертывания, с именем **custom.json**:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.docker.repository=<your-docker-repository>"
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.docker.registry=<your-docker-registry>"
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.docker.imageTag=<your-docker-image-tag>"
```

Развертывание запрашивает имя пользователя docker и пароль, или можно указать их в **DOCKER_USERNAME** и **DOCKER_PASSWORD** переменных среды.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании кластера больших данных, см. в разделе [развертывание больших данных в SQL Server кластеров Kubernetes](deployment-guidance.md).
