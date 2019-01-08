---
title: Развертывать группу доступности SQL Server Always On, в кластере Kubernetes
description: В этой статье описывается параметры для SQL Server Kubernetes Always On доступности группы оператор глобальным требованиям
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4b42f0a70765744147a44c8b4d274b87cc00ca43
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215430"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Развертывать группу доступности SQL Server Always On, в кластере Kubernetes

В этой статье пример развертывает группу доступности SQL Server Always On, в кластере Kubernetes с тремя репликами. Вторичные реплики находятся в режиме синхронной фиксации.

На платформе Kubernetes, развертывание включает оператор SQL Server, SQL Server контейнеры и нагрузки служб балансировки. Оператор автоматически управляет группы доступности. В этой статье объясняется, как:

- Развертывание, оператор, контейнеры SQL Server и службы балансировки нагрузки.
- Подключение к группе доступности со службами.
- Добавление базы данных к группе доступности.

## <a name="requirements"></a>Требования

- Кластер Kubernetes
- Kubernetes версии 1.11.0 или более поздней версии
- По крайней мере три узла
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Доступ к [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) репозитория GitHub

> [!NOTE]
> Можно использовать любой тип кластера Kubernetes. Чтобы создать кластер Kubernetes в службе Azure Kubernetes (AKS), см. в разделе [создание кластера AKS](https://docs.microsoft.com/azure/aks/create-cluster).
> Следующий скрипт создает четырех узлов кластера Kubernetes в Azure.
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.3 --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Развертывание оператор, контейнеры SQL Server и службы балансировки нагрузки

1. Создание [пространства имен](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

      В этом примере используется пространство имен с именем `ag1`. Выполните следующую команду, чтобы создать пространство имен.
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      Все объекты, принадлежащие к этому решению находятся в `ag1` пространства имен.

1. Настройте и разверните манифест оператор SQL Server.

      Копирование SQL Server [ `operator.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) файла из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      `operator.yaml` Файла есть манифест развертывания для оператора Kubernetes.
    
      Применить манифест к кластеру Kubernetes.
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Создание секрета для Kubernetes с паролями для `sa` учетной записи и главный ключ экземпляра SQL Server.

      Создайте секрет с `kubectl`.
      
      В следующем примере создается с именем секрета `sql-secrets` в `ag1` пространства имен. Секрет хранит два пароля:
      
      - `sapassword` хранит пароль для SQL Server `sa` учетной записи.
      - `masterkeypassword` сохраняет пароль, используемый для создания главного ключа SQL Server. 
    
   Скопируйте сценарий в свой терминал. Замените каждый `<>` сложный пароль и выполните сценарий, чтобы создать секрет.
    
   >[!NOTE]
   >Нельзя использовать пароль `&` или `` ` `` символов.
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. Развертывание пользовательских ресурсов SQL Server.

      Скопируйте манифест SQL Server [ `sqlserver.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      >[!NOTE]
      >`sqlserver.yaml` Файл описывает контейнеры SQL Server, утверждения постоянного тома, постоянные тома и службы балансировки нагрузки, которые требуются для каждого экземпляра SQL Server.
    
      Применить манифест к кластеру Kubernetes.
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
На следующем рисунке показано успешное применение `kubectl apply` для этого примера.

![Создание sqlservers](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

После установки SQL Server манифеста оператор развертывает контейнеры SQL Server.

Kubernetes размещает контейнеры в модули. Используйте `kubectl get pods --namespace ag1` для просмотра состояния модулей POD. Ниже приведен пример развертывания после развертывания модулей SQL Server. 

![встроенные модули](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Мониторинг развертывания

Можно использовать [панели мониторинга Kubernetes со службой Azure Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) мониторинге развертывания.

Используйте `az aks browse` для запуска панели мониторинга. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Подключение к группе доступности с помощью служб

[ `ag-services.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) Из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) пример описывает службы балансировки нагрузки, которые могут подключаться к репликам группы доступности. 

- `ag1-primary` предоставляет конечную точку для подключения к первичной реплике.
- `ag1-secondary` предоставляет конечную точку для подключения к любой вторичной реплике.

При применении файл манифеста Kubernetes создаст служб балансировки нагрузки для каждого типа репликации. Службе балансировки нагрузки содержит IP-адресом. Используйте этот IP-адрес для подключения к типу реплики, что нужно.

Для развертывания служб, выполните следующую команду.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

После развертывания службы, использовать `kubectl get services --namespace ag1` для определения IP-адрес для службы.

IP-адресом подключаются к экземпляру SQL Server, на котором размещена реплика каждого типа.

На следующем рисунке:

- В результате `kubectl get services` для пространства имен `ag1`.

- Службы балансировки нагрузки, которые создаются для каждого контейнера SQL Server. Используйте эти IP-адреса как конечные точки для подключения непосредственно к экземплярам SQL Server в кластере.

- `sqlcmd` Подключения к первичной реплике, с помощью `sa` учетной записи через конечную точку подсистемы балансировки нагрузки.

![Подключение](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных в группу доступности

>[!NOTE]
>В настоящее время SQL Server Management Studios не удается добавить базу данных в группу доступности. С помощью Transact-SQL.

После того как Kubernetes создаст контейнеры SQL Server, выполните следующие действия, чтобы добавить базу данных к группе доступности.

1. [Подключение](sql-server-linux-kubernetes-connect.md) к экземпляру SQL Server в кластере.

1. Создание базы данных.

      ```sql
      CREATE DATABASE [demodb]
      ```

1. Создание полной резервной копии базы данных, чтобы начать цепочку журналов.

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. Добавьте базу данных к группе доступности.

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
Эта группа доступности создается с помощью автоматического заполнения, чтобы SQL Server автоматически создает вторичные реплики.

Можно просмотреть состояние группы доступности с помощью панели мониторинга группы обеспечения доступности SQL Server Management Studio.

![панель мониторинга](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Следующие шаги

- [Подключение к группе доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-connect.md)

- [Управлять группой доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-manage.md)

- [SQL Server поддерживает группы доступности на контейнеры в кластере Kubernetes](sql-server-ag-kubernetes.md)
