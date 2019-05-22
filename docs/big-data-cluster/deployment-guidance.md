---
title: Руководства по развертыванию
titleSuffix: SQL Server big data clusters
description: Дополнительные сведения о развертывании кластеров SQL Server 2019 больших данных (Предварительная версия) на платформе Kubernetes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 924d026c61275d5bc957ce1157e30381f27ef2d0
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993985"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Развертывание кластеров больших данных SQL Server в Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Большие данные кластера SQL Server развертывается как контейнеры docker в кластере Kubernetes. Это этапы установки и настройки:

- Настройка кластера Kubernetes в одиночной ВМ, кластера виртуальных машин или в службе Azure Kubernetes (AKS).
- Установите средство конфигурации кластера **mssqlctl** на клиентском компьютере.
- Развертывание кластера больших данных SQL Server в кластере Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Установка средств SQL Server 2019 больших данных

Перед развертыванием кластера SQL Server 2019 больших данных, сначала [установите средства работы с большими данными](deploy-big-data-tools.md):

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **Расширение SQL Server 2019**

## <a id="prereqs"></a> Предварительные требования для Kubernetes

Кластерами больших данных SQL Server требуется по меньшей мере минимальной версии Kubernetes v1.10 для сервера и клиента (kubectl).

> [!NOTE]
> Обратите внимание, что Kubernetes версии клиента и сервера не может превышать + 1 или -1, дополнительный номер версии. Дополнительные сведения см. в разделе [Kubernetes поддерживаемые выпуски и наклона компонент](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a> Настройка кластера Kubernetes

Если у вас уже есть кластер Kubernetes, соответствующий требованиям выше, то вы можете сразу переходить к [шаг развертывания](#deploy). В этом разделе требуется понимание основных концепций Kubernetes.  Подробные сведения о Kubernetes см. в разделе [документации по Kubernetes](https://kubernetes.io/docs/home).

Вы можете развернуть Kubernetes в любом из трех способов:

| Развертывание Kubernetes на: | Описание | Ссылка |
|---|---|---|
| **Службы Azure Kubernetes (AKS)** | Управляемой службы контейнеров Kubernetes в Azure. | [Инструкции](deploy-on-aks.md) |
| **Несколько компьютеров (kubeadm)** | Кластер Kubernetes, развернутых на физических компьютерах или виртуальных машин с помощью **kubeadm** | [Инструкции](deploy-with-kubeadm.md) |
| **Minikube** | Кластер Kubernetes одного узла на виртуальной Машине. | [Инструкции](deploy-on-minikube.md) |

> [!TIP]
> Пример скрипта python, выполняющий развертывание AKS и SQL Server, больших данных в кластер в один шаг, см. в разделе [краткое руководство: Развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md).

### <a name="verify-kubernetes-configuration"></a>Проверка конфигурации Kubernetes

Запустите **kubectl** команду, чтобы просмотреть конфигурацию кластера. Убедитесь, что этот kubectl указывает контекст правильный кластера.

```bash
kubectl config view
```

После настройки кластера Kubernetes, можно продолжить развертывание нового кластера больших данных SQL Server. Если при обновлении с предыдущей версии, ознакомьтесь с разделом [обновление кластеров SQL Server с большими данными](deployment-upgrade.md).

## <a id="deploy"></a> Общие сведения о развертывании

Начиная с CTP-версии 2.5, большинство параметров кластера больших данных определены в JSON-файлу конфигурации развертывания. Вы можете использовать профиль развертывания по умолчанию для AKS, kubeadm, или minikube или вы можете настроить свой собственный файл конфигурации развертывания для использования во время установки. По соображениям безопасности параметры проверки подлинности, передаются через переменные среды.

Следующие разделы содержат дополнительные сведения о настройке большие данные кластер развертываний, а также примеры общих настроек. Кроме того можно всегда изменить файл конфигурации развертывания, используя редактор, такой как VSCode, например.

## <a id="configfile"></a> Конфигурации по умолчанию

Развертывания, параметры определяются в файлах конфигурации JSON кластера больших данных. Существует три профиля стандартное развертывание с параметрами по умолчанию для среды разработки и тестирования.

| Профиль развертывания | Среды Kubernetes |
|---|---|
| **aks-dev-test.json** | Служба Azure Kubernetes (AKS) |
| **kubeadm-dev-test.json** | Несколько компьютеров (kubeadm) |
| **minikube-dev-test.json** | Minikube |

Можно развернуть кластер больших данных, выполнив **создания кластера mssqlctl**. Это приглашение выбрать одну из конфигураций по умолчанию и затем поможет выполнить развертывание.

```bash
mssqlctl cluster create
```

> [!TIP]
> В этом примере будут запрошены все параметры, которые не являются частью конфигурации по умолчанию, такие как пароли. Обратите внимание, что данные Docker предоставляется вам корпорацией Майкрософт как часть 2019 сервера SQL [программе раннего освоения](https://aka.ms/eapsignup).

## <a id="customconfig"></a> Пользовательские конфигурации

Можно также настроить свой собственный файл конфигурации развертывания. Это можно сделать, выполнив следующие действия:

1. Начните с одного из профилей, стандартного развертывания, которые соответствуют вашей среде Kubernetes. Можно использовать **список конфигурации кластеров mssqlctl** команду, чтобы перечислить их:

   ```bash
   mssqlctl cluster config list
   ```

1. Чтобы настроить развертывание, создать копию профиля развертывания с помощью **init конфигурации кластера mssqlctl** команды. Например, следующая команда создает копию **aks-dev-test.json** файл конфигурации развертывания в текущем каталоге:

   ```bash
   mssqlctl cluster config init --src aks-dev-test.json --target custom.json
   ```

1. Чтобы настроить параметры в файле конфигурации развертывания, его можно изменить при помощи инструмента, который хорошо подходит для редактирования документы json, как и VS Code. Для сценариев автоматизации, можно изменить файл конфигурации с помощью **набор раздел конфигурации кластера mssqlctl** команды. Например, следующая команда изменяет пользовательский файл конфигурации можно изменить имя развернутого кластера по умолчанию (**mssql-cluster**) для **тестового кластера**:  

   ```bash
   mssqlctl cluster config section set --config-file custom.json --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > — Это полезное средство для поиска путей JSON [JSONPath Online вычислителя](https://jsonpath.com/).

   Помимо передачи пары "ключ значение", можно также предоставляют встроенные значения JSON или передать файлы исправления JSON. Дополнительные сведения см. в разделе [настроить параметры развертывания для больших данных кластеров](deployment-custom-configuration.md).

1. Затем передать настраиваемый файл конфигурации для **создания кластера mssqlctl**. Обратите внимание, что необходимо задать требуемый [переменные среды](#env), в противном случае вам будет предложено ввести значения:

   ```bash
   mssqlctl cluster create --config-file custom.json --accept-eula yes
   ```

> [!TIP]
> Дополнительные сведения о структуре файла конфигурации развертывания, см. в разделе [ссылка на файл конфигурации развертывания](reference-deployment-config.md). Дополнительные примеры настройки, см. в разделе [настроить параметры развертывания для больших данных кластеров](deployment-custom-configuration.md).

## <a id="env"></a> Переменные среды

Для параметров безопасности, которые не хранятся в файле конфигурации развертывания используются следующие переменные среды. Обратите внимание на то, что параметры Docker, за исключением учетных данных может быть задано в файле конфигурации.

| Переменная среды | Описание |
|---|---|---|---|
| **DOCKER_USERNAME** | Имя пользователя для доступа к образы контейнеров, в случае, если они хранятся в частный репозиторий. |
| **DOCKER_PASSWORD** | Пароль для доступа к выше частный репозиторий. |
| **CONTROLLER_USERNAME** | Имя пользователя администратора кластера. |
| **CONTROLLER_PASSWORD** | Пароль администратора кластера. |
| **KNOX_PASSWORD** | Пароль для пользователя Knox. |
| **MSSQL_SA_PASSWORD** | Пароль пользователя SA для главного экземпляра SQL. |

Эти переменные среды задаются до вызова метода **создания кластера mssqlctl**. Если любой переменной не задано, запросит его.

В следующем примере показано, как задать переменные среды для Linux (bash) и Windows (PowerShell):

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
export DOCKER_USERNAME=<docker-username>
export DOCKER_PASSWORD=<docker-password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
SET DOCKER_USERNAME=<docker-username>
SET DOCKER_PASSWORD=<docker-password>
```

После настройки переменных среды, необходимо запустить `mssqlctl cluster create` для инициации развертывания. В этом примере используется файл конфигурации кластера, созданный выше:

```
mssqlctl cluster create --config-file custom.json --accept-eula yes
```

Обратите внимание, приведенным ниже рекомендациям:

- В настоящее время учетные данные для частного реестра Docker будет предоставляться вам после рассмотрения вашего [программе раннего освоения регистрации](https://aka.ms/eapsignup). Для тестовых кластеров больших данных в SQL Server требуется раннего внедрения программы регистрации.
- Убедитесь, что перенос паролей в двойные кавычки, если он содержит специальные символы. Можно задать **MSSQL_SA_PASSWORD** на все, что вы, например, но убедитесь, что пароль недостаточно сложен и не используйте `!`, `&` или `'` символов. Обратите внимание, что двойные кавычки-разделители работают только в команды bash.
- **SA** имя входа является системным администратором на основной экземпляр SQL Server, который создается во время установки. После создания контейнера SQL Server, **MSSQL_SA_PASSWORD** переменной среды, которые вы указали может быть обнаружен, выполнив echo MSSQL_SA_PASSWORD $ в контейнере. В целях безопасности смените пароль SA в соответствии с практическими рекомендациями, описанными [здесь](../linux/quickstart-install-connect-docker.md#sapassword).

## <a id="unattended"></a> Автоматическая установка

Для автоматического развертывания, необходимо задать все необходимые переменные среды, используйте файл конфигурации и вызов `mssqlctl cluster create` с `--accept-eula yes` параметра. В предыдущем разделе примерах синтаксиса для автоматической установки.

## <a id="monitor"></a> Мониторинг развертывания

Во время начальной загрузки кластера командное окно клиента будет выводить состояние развертывания. Во время развертывания вы увидите ряд сообщений где ожидает pod контроллера:

```output
2019-04-12 14:40:10.0129 UTC | INFO | Waiting for controller pod to be up...
```

Меньше 15 – 30 минут вы должны быть уведомлены выполняющийся модуль контроллера:

```output
2019-04-12 15:01:10.0809 UTC | INFO | Waiting for controller pod to be up. Checkthe mssqlctl.log file for more details.
2019-04-12 15:01:40.0861 UTC | INFO | Controller pod is running.
2019-04-12 15:01:40.0884 UTC | INFO | Controller Endpoint: https://<ip-address>:30080
```

> [!IMPORTANT]
> Всего развертывание может занять много времени из-за время, необходимое для загрузки образов контейнеров для компонентов кластера больших данных. Тем не менее он должен занять несколько часов. При возникновении проблем с развертыванием, см. в разделе [мониторинг и устранение неполадок с кластерами больших данных SQL Server](cluster-troubleshooting-commands.md).

После завершения развертывания, уведомляет о выходных данных успеха.

```output
2019-04-12 15:37:18.0271 UTC | INFO | Monitor and track your cluster at the Portal Endpoint: https://<ip-address>:30777/portal/
2019-04-12 15:37:18.0271 UTC | INFO | Cluster deployed successfully.
```

Обратите внимание, URL-адрес **конечной точки портала** в предыдущих выходных данных для использования в следующем разделе.

> [!TIP]
> Имя по умолчанию для кластера развернутой больших данных — `mssql-cluster` Если пользовательской конфигурации.

## <a id="endpoints"></a> Получить конечные точки

После успешного выполнения сценария развертывания, можно получить IP-адреса внешних конечных точек для больших данных кластера, выполнив следующие действия.

1. После развертывания, найти IP-адрес конечной точки контроллера на внешний IP-данными, полученными следующей **kubectl** команды:

   ```bash
   kubectl get svc controller-svc-external -n <your-cluster-name>
   ```

1. Войдите кластер больших данных с **mssqlctl входа**. Задайте **--конечной точки контроллера** параметр внешний IP-адрес конечной точки контроллера.

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Укажите имя пользователя и пароль, настроенный для контроллера (CONTROLLER_USERNAME и CONTROLLER_PASSWORD) во время развертывания.

1. Запустите **списка конечных точек кластера mssqlctl** для получения списка с описанием каждой конечной точки и соответствующих IP адрес и порт. 

   ```bash
   mssqlctl cluster endpoint list
   ```

   В следующем списке приведены пример выходных данных этой команды:

   ```output
   Name               Description                                             Endpoint                                                   Ip              Port    Protocol
   -----------------  ------------------------------------------------------  ---------------------------------------------------------  --------------  ------  ----------
   gateway            Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  30443   https
   spark-history      Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  30443   https
   yarn-ui            Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  30443   https
   app-proxy          Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  30778   https
   management-proxy   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  30777   https
   portal             Management Portal                                       https://11.111.111.111:30777/portal                        11.111.111.111  30777   https
   log-search-ui      Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  30777   https
   metrics-ui         Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  30777   https
   controller         Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  30080   https
   sql-server-master  SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  31433   tcp
   webhdfs            HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  30443   https
   livy               Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  30443   https
   ```

### <a name="minikube"></a>Minikube

Если вы используете minikube, необходимо выполнить следующую команду, чтобы получить IP-адрес, необходимые для подключения к. В дополнение к IP-адрес укажите порт для конечной точки, необходимые для подключения к.

```bash
minikube ip
```

Независимо от платформы запуске кластера Kubernetes, чтобы получить все конечные точки служб, развернутых для кластера, выполните следующую команду:

```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="connect"></a> Подключитесь к кластеру

Дополнительные сведения о том, как подключиться к кластеру больших данных, см. в разделе [соединиться с сервером SQL кластера больших данных с помощью Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о развертывании кластера больших данных, см. следующие ресурсы:

- [Настройка параметров развертывания для больших данных кластеров](deployment-custom-configuration.md)
- [Выполнение автономного развертывания кластера больших данных SQL Server](deploy-offline.md)
- [Семинар: Кластерами больших данных Microsoft SQL Server архитектуры](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
