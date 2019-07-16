---
title: Создание скриптов развертывания для SQL Server группы доступности AlwaysOn в Kubernetes
description: В этой статье объясняется, как создать скрипты развертывания для SQL Server всегда группу доступности в Kubernetes
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 181773a19e87c34a1931cae05f5a329aedbc1239
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000140"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>Создать скрипт развертывания для SQL Server группы доступности AlwaysOn

В этой статье описывается развертывание группы доступности в кластере Kubernetes в рамках одной команды с пример сценария развертывания. `deploy-ag.py` — Это сценарий Python, который создает `.yaml` файлов для кластера и их можно применить к кластеру Kubernetes.

Загрузка файлов из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script).

## <a name="before-you-start"></a>Перед началом

Установите следующие средства на рабочей станции.

* [Python](https://www.python.org/downloads/) (3.5 или 3.6)
* [PyYAML](https://pyyaml.org/) -пакетов Python
* [Клиент Kubernetes](https://github.com/kubernetes-client/python) — пакет Python

Добавьте пути python к переменным среды (для Windows).

### <a name="install-the-required-components"></a>Установка необходимых компонентов

В следующем примере, указанных выше устанавливаются пакеты PyYAML и клиент Kubernetes для Python.

После установки Python, загрузите и извлеките папки образца. 

Чтобы настроить необходимые файлы, выполните следующую команду. Замените `<path>` с расположением файлов извлеченном образце.

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>Создание кластера и загрузить файл конфигурации

В следующем примере создается кластер в службе Azure Kubernetes (AKS).

Прежде чем выполнять скрипт, обновите значения в угловых скобках - `<>`.

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>Группы доступности требуется Kubernetes версии 1.11.0 или более поздней версии. В примере указывается 1.11.1.

## <a name="run-the-deployment-script"></a>Запуск скрипта развертывания

Следующие примеры демонстрируют, как выполнять `deploy-ag.py`.

### <a name="help"></a>Help

```cmd
python ./deploy-ag.py --help
```

* **Использование**: `deploy-ag.py [-h] {deploy | failover} ...`
* **необязательные аргументы**:
  * `-h, --help` Отображение этого справочного сообщения и выход
* **подкоманды**:
  * Действия на агенте k8s {развертывание | отработки отказа}

  `deploy`

   Развертывание набора серверов SQL Server в группе доступности

  `failover`

   Отработка отказа на целевой реплике.

### <a name="deploy-help"></a>Развертывание справки

```cmd
python ./deploy-ag.py deploy --help
```

* **Использование**:

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  Развертывание SQL Server и k8s агентов в namespace(AG name)

* **необязательные аргументы**:
  
  `-h, --help`
  
  Отображение этого справочного сообщения и выход
  
  `--verbose, -v`
  
  Уровень детализации выходных данных
  
  `--ag AG`
  
  Имя группы доступности. По умолчанию = ag1
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  Имя пространства имен k8s. По умолчанию используется имя группы Доступности, если не указано.

  `--dry-run`
  
  Создание манифестов, но не применяются.
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  имена экземпляров SQL Server (до 5, разделяя их пробелами) по умолчанию = [«mssql1», «mssql2», «mssql3»]
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  Пароль системного Администратора. По умолчанию = «SAPassword2018»
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  Пропустить создание пространства имен.

### <a name="failover-help"></a>Справка отработки отказа

```cmd
python ./deploy-ag.py failover --help
```
* **Использование**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  Вручную выполните отработку отказа

* **позиционные аргументы**: `target_replica`

  Имя целевого SQL Server реплики для отработки отказа

* **необязательные аргументы**:

  `-h, --help`
  
  Отображение этого справочного сообщения и выход

  `--verbose, -v`
  
  Уровень детализации выходных данных

  `--ag AG`
  
  Имя группы доступности. По умолчанию = ag1

  `--namespace NAMESPACE`

  Имя пространства имен k8s. Значение по умолчанию — имя группы Доступности, если не указан

  `--dry-run`
  
  Создать, но не применяются манифестов.

### <a name="create-the-manifests---dont-apply"></a>Создание манифестов - неприменимы

Следующий скрипт создает файлы манифеста, но не применяются.

```cmd
python ./deploy-ag.py deploy --dry-run
```

В следующем примере создается манифесты для группы доступности в пространстве имен `AG1` с тремя репликами. Перед выполнением скрипта замените `<MyC0m91exP@55w0r!>` сложный пароль.

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

Предыдущая команда создает файлы yaml-файл в каталоге.

В этом случае выходных данных команды показано, где создаются файлы манифеста.

![выходные данные сценария](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>Создание манифестов и применение

В следующем примере создается манифесты для группы доступности в пространстве имен `ag1` с тремя репликами и применяет его к кластеру Kubernetes. Кластер автоматически создаст группу доступности. Перед выполнением скрипта замените `<MyC0m91exP@55w0r!>` сложный пароль.

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

После завершения сценария, оператор Kubernetes создает хранилище, экземпляры SQL Server, службы подсистемы балансировки нагрузки. Вы можете отслеживать развертывание с помощью [панели мониторинга Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard).

После того как Kubernetes создаст контейнеры SQL Server:

1. [Подключение](sql-server-linux-kubernetes-connect.md) к экземпляру SQL Server в кластере.

1. Создание базы данных.

1. Создание полной резервной копии базы данных, чтобы начать цепочку журналов.

1. Добавьте базу данных к группе доступности.

Группы доступности создается с помощью автоматического заполнения, поэтому SQL Server автоматически создаст соответствующие репликах базы данных-получатели.

### <a name="manually-failover"></a>Вручную выполните отработку отказа

В следующем примере отработка отказа первичной реплики.

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>Следующие шаги

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
