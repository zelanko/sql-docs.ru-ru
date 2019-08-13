---
title: Создание скриптов развертывания для группы доступности Always On SQL Server в Kubernetes
description: Эта статья описывает создание скриптов развертывания для группы доступности Always On SQL Server в Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 181773a19e87c34a1931cae05f5a329aedbc1239
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68000140"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>Создание скриптов развертывания для группы доступности Always On SQL Server

Эта статья описывает, как развернуть группу доступности в кластере Kubernetes с помощью одной команды с использованием примера скрипта развертывания. `deploy-ag.py` — это скрипт Python, который создает файлы `.yaml` для кластера и может применить их к кластеру Kubernetes.

Скачайте файл с файлами из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script).

## <a name="before-you-start"></a>Перед началом

Установите на рабочую станцию следующие средства.

* [Python](https://www.python.org/downloads/) (3.5 или 3.6)
* [PyYAML](https://pyyaml.org/) — пакеты Python
* [Клиент Kubernetes](https://github.com/kubernetes-client/python) — пакет Python

Добавьте пути Python в переменные среды (для Windows).

### <a name="install-the-required-components"></a>Установка необходимых компонентов

Следующий пример устанавливает для Python пакеты с PyYAML и клиентом Kubernetes.

Установив Python, скачайте и извлеките пример папки. 

Чтобы настроить необходимые файлы, выполните приведенную ниже команду. Замените `<path>` на расположение с извлеченными примерами файлов.

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>Создание кластера и скачивание файла конфигурации

Следующий пример создает кластер в службе Azure Kubernetes (AKS).

Перед выполнением скрипта обновите значения в угловых скобках — `<>`.

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>Для групп доступности требуется Kubernetes версии 1.11.0 или более поздней. Для примера указана версия 1.11.1.

## <a name="run-the-deployment-script"></a>Выполнение скрипта развертывания

Выполнение `deploy-ag.py` продемонстрировано в следующих примерах.

### <a name="help"></a>Справка

```cmd
python ./deploy-ag.py --help
```

* **Использование**: `deploy-ag.py [-h] {deploy | failover} ...`
* **Дополнительные аргументы**:
  * `-h, --help` — отображение этого справочного сообщения и выход
* **Подкоманды**
  * Действия на агенте k8s {deploy | failover}

  `deploy`

   Развертывание набора серверов SQL Server в группе доступности

  `failover`

   Отработка отказа в целевую реплику

### <a name="deploy-help"></a>Справка по deploy

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

  развертывание SQL Server и агентов k8s в пространстве имен (имя группы доступности)

* **Дополнительные аргументы**:
  
  `-h, --help`
  
  отображение этого справочного сообщения и выход
  
  `--verbose, -v`
  
  Уровень детализации выходных данных
  
  `--ag AG`
  
  Имя группы доступности. По умолчанию: ag1.
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  Имя пространства имен k8s. Если не указано, по умолчанию используется имя группы доступности.

  `--dry-run`
  
  Создание манифестов без их применения.
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  Имена экземпляров SQL Server (до 5, разделенные пробелами). По умолчанию: ['mssql1', 'mssql2', 'mssql3']
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  Пароль системного администратора. По умолчанию: "SAPassword2018"
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  Пропуск создания пространства имен.

### <a name="failover-help"></a>Справка по failover

```cmd
python ./deploy-ag.py failover --help
```
* **Использование**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  отработка отказа вручную

* **Позиционные аргументы**: `target_replica`

  имя целевой реплики SQL Server для отработки отказа

* **Дополнительные аргументы**:

  `-h, --help`
  
  отображение этого справочного сообщения и выход

  `--verbose, -v`
  
  Уровень детализации выходных данных

  `--ag AG`
  
  Имя группы доступности. По умолчанию: ag1.

  `--namespace NAMESPACE`

  Имя пространства имен k8s. Если не указано, по умолчанию используется имя группы доступности.

  `--dry-run`
  
  Создание манифестов без их применения.

### <a name="create-the-manifests---dont-apply"></a>Создание манифестов без их применения

Следующий скрипт создает файлы манифеста, но не применяет их.

```cmd
python ./deploy-ag.py deploy --dry-run
```

Следующий пример создает манифесты для группы доступности в пространстве имен `AG1` с тремя репликами. Перед запуском скрипта замените `<MyC0m91exP@55w0r!>` сложным паролем.

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

Предыдущая команда создает каталог для примеров YAML-файлов.

В этом случае выходные данные команды показывают, где создаются файлы манифеста.

![выходные данные скрипта](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>Создание и применение манифестов

Следующий пример создает манифесты для группы доступности в пространстве имен `ag1` с тремя репликами и применяет их к кластеру Kubernetes. Затем кластер создает группу доступности. Перед запуском скрипта замените `<MyC0m91exP@55w0r!>` сложным паролем.

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

После завершения скрипта оператор Kubernetes создает хранилище, экземпляры SQL Server, службы балансировки нагрузки. Вы можете отслеживать развертывание с помощью [панели мониторинга Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard).

После того как Kubernetes создает контейнеры SQL Server, выполните следующее.

1. [Подключитесь](sql-server-linux-kubernetes-connect.md) к экземпляру SQL Server в кластере.

1. Создание базы данных.

1. Создайте полную резервную копию базы данных, чтобы начать цепочку журналов.

1. Добавьте базу данных в группу доступности.

Группа доступности создается с автоматическим заполнением, поэтому SQL Server будет автоматически создавать базы данных-получатели в соответствующих репликах.

### <a name="manually-failover"></a>отработка отказа вручную

В следующем примере выполняется отработка отказа первичной реплики.

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>Следующие шаги

[Группа доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
