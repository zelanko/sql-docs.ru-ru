---
title: Развертывание в автономном режиме
titleSuffix: SQL Server big data clusters
description: Сведения о том, как выполнить автономное развертывание кластера больших данных SQL Server.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 15af041e94ac0abfdae13635345de62262a4b086
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531976"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Выполнение автономного развертывания кластера больших данных SQL Server

В этой статье описывается процедура автономного развертывания [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Кластеры больших данных должны иметь доступ к репозиторию Docker, из которого извлекаются образы контейнеров. При автономной установке требуемые образы помещаются в частный репозиторий Docker. Затем этот частный репозиторий используется в качестве источника образов для нового развертывания.

## <a name="prerequisites"></a>предварительные требования

- Docker Engine 1.8+ на любом поддерживаемом дистрибутиве Linux или Docker для Mac или Windows. Дополнительные сведения см. в разделе [Установка Docker](https://docs.docker.com/engine/installation/).

## <a name="load-images-into-a-private-repository"></a>Загрузка образов в частный репозиторий

Ниже описано, как извлечь образы контейнеров кластера больших данных из репозитория Майкрософт, а затем отправить их в ваш частный репозиторий.

> [!TIP]
> Приведенные ниже шаги показывают, как это сделать. Однако для упрощения задачи вместо выполнения этих команд вручную можно использовать [автоматический скрипт](#automated).

1. Извлеките образы контейнеров кластера больших данных, выполняя указанную ниже команду. Замените `<SOURCE_IMAGE_NAME>` на [имя каждого из образов](#images). Замените `<SOURCE_DOCKER_TAG>` тегом для выпуска кластера больших данных, например **2019-GDR1-ubuntu-16.04**.  

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
- **mssql-control-watchdog**
- **mssql-controller**
- **mssql-dns**
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
- **mssql-security-domainctl**
- **mssql-security-knox**
- **mssql-security-support**
- **mssql-server**
- **mssql-server-controller**
- **mssql-server-data**
- **mssql-ha-operator**
- **mssql-ha-supervisor**
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
   python push-bdc-images-to-custom-private-repo.py
   ```

   **Linux:**

   ```bash
   sudo python push-bdc-images-to-custom-private-repo.py
   ```

1. Следуйте инструкциям на экране, чтобы ввести сведения о репозитории Майкрософт и частном репозитории. После завершения выполнения скрипта все необходимые образы должны находиться в частном репозитории.

1. Следуйте инструкциям [здесь](deployment-custom-configuration.md#docker), чтобы узнать, как настроить файл конфигурации развертывания `control.json`, чтобы использовать реестр и репозиторий контейнеров. Обратите внимание, что перед развертыванием необходимо задать переменные среды `DOCKER_USERNAME` и `DOCKER_PASSWORD`, чтобы разрешить доступ к частному репозиторию.

## <a name="install-tools-offline"></a>Автономная установка средств

Для развертывания кластеров больших данных нужно несколько средств, включая **Python**, `azdata` и **kubectl**. Чтобы установить эти средства на автономном сервере, выполните указанные ниже действия.

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

1. На компьютере с доступом в Интернет и [Python](https://wiki.python.org/moin/BeginnersGuide/Download) выполните приведенную ниже команду, чтобы скачать все пакеты `azdata` в текущую папку.

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. Скопируйте скачанные пакеты и файл `requirements.txt` на целевой компьютер.

1. Выполните указанную ниже команду на целевом компьютере, указав папку, куда вы скопировали предыдущие файлы.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a> Автономная установка kubectl

Чтобы установить **kubectl** на автономный компьютер, выполните указанные ниже действия.

1. Используйте **curl**, чтобы скачать **kubectl** в выбранную вами папку. Дополнительные сведения см. в разделе [Установка двоичного файла kubectl с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl).

1. Скопируйте эту папку на целевой компьютер.

## <a name="deploy-from-private-repository"></a>Развертывание из частного репозитория

Для развертывания из частного репозитория выполните действия, описанные в [руководстве по развертыванию](deployment-guidance.md), но используйте пользовательский файл конфигурации развертывания, в котором указаны сведения о вашем частном репозитории Docker. Следующие команды `azdata` демонстрируют, как изменить параметры Docker в пользовательском файле конфигурации развертывания с именем `control.json`.

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

При развертывании отображается запрос на ввод имени пользователя и пароля Docker, либо их можно указать в переменных среды `DOCKER_USERNAME` и `DOCKER_PASSWORD`.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании кластеров больших данных см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md).
