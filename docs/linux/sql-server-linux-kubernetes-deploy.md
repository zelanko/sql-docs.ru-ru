---
title: Развертывание SQL Server AlwaysOn группы доступности в кластере Kubernetes
description: В этой статье описывается параметры для SQL Server Kubernetes Always On доступности группы оператор глобальным требованиям
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4d24cd2ab59e1a7959f5a8ac1c929ff2e5e8e54a
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049604"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-kubernetes-cluster"></a>Развертывание SQL Server Always On группы доступности в кластере Kubernetes

## <a name="requirements"></a>Требования

- Кластер Kubernetes
- Kubernetes версии 1.11.0 или более поздней версии
- Четыре или более узлов
- [kubectl](http://kubernetes.io/docs/tasks/tools/install-kubectl/).

  >[!NOTE]
  >Можно использовать любой тип кластера Kubernetes. Чтобы создать кластер Kubernetes в службе Azure Kubernetes (AKS), см. в разделе [создание кластера AKS](http://docs.microsoft.com/azure/aks/create-cluster.md).
  > Следующий скрипт создает четыре узла кластера Kubernetes в Azure.
  >```azure-cli
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.1
  >```

## <a name="steps"></a>Шаги

1. Настройка хранилища

  В облачных средах, как Azure, настройте [постоянные тома](http://kubernetes.io/docs/concepts/storage/persistent-volumes/) для каждого экземпляра SQL Server.

  Чтобы создать постоянные тома в Azure, см. в разделе `pv.yaml` и `pvc.yaml` в [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates).

  Чтобы создать хранилище, выполните следующую команду:

  ```azurecli
  kubectl apply -f <pv.yaml>
  ```

1. Создайте секреты Kubernetes пароль SA и главный ключ.

  В следующем примере создается два секрета. `sapassword` — пароль SA и `masterkeypassword` — для главного ключа. Перед запуском скрипта эта функция заменяет `<MyC0mp13xP@55w04d!>` другой сложный пароль для каждого секрета.

   ```azurecli
   kubectl create secret generic sql-secrets --from-literal='sapassword=<MyC0mp13xP@55w04d!>' --from-literal='masterkeypassword=<MyC0mp13xP@55w04d!>'
   ```

1. Настройте и разверните манифест оператор SQL Server.

  Скопируйте оператора SQL Server `operator.yaml` файла из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  `operator.yaml` Файл является manifiest развертывания для оператора Kubernetes.

  Чтобы настроить манифест, обновите `operator.yaml` файл для вашей среды.

  Применить манифест к кластеру Kubernetes.

  ```azurecli
  kubectl apply -f operator.yaml
  ```

1. Развертывание пользовательских ресурсов SQL Server.

  Скопируйте манифест SQL Server `sqlserver.yaml` из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Применить манифест к кластеру Kubernetes.

  ```azurecli
  kubectl apply -f sqlserver.yaml
  ```

После развертывания SQL Server манифест, оператор развертывает экземпляры SQL Server в качестве модулей в контейнерах.

После завершения сценария, оператор Kubernetes создаст хранилище, экземпляры SQL Server, службы подсистемы балансировки нагрузки. Вы можете отслеживать развертывание с помощью [панели мониторинга Kubernetes](http://docs.microsoft.com/azure/aks/kubernetes-dashboard).

После того как Kubernetes создаст контейнеры SQL Server выполните следующие действия, чтобы добавить базу данных к группе доступности.

1. [Подключение](sql-server-linux-kubernetes-connect.md) к экземпляру SQL Server в кластере.

1. Создание базы данных.

1. Создание полной резервной копии базы данных, чтобы начать цепочку журналов.

1. Добавьте базу данных к группе доступности.

Эта группа доступности создается с помощью автоматического заполнения, поэтому SQL Server автоматически создает вторичные реплики.

## <a name="next-steps"></a>Следующие шаги

[Подключиться к группе доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-connect.md)

[Управление группой доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-manage.md)

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)