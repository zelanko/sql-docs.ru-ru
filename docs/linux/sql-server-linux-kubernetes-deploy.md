---
title: Развертывание группы доступности Always On SQL Server в кластере Kubernetes
description: В этой статье объясняются параметры для глобальных требований к оператору группы доступности Always On SQL Server в Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a4811c1f41c4c8b9a566dc13b3de713576b4980d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952629"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Развертывание группы доступности Always On SQL Server в кластере Kubernetes

Пример в этой статье развертывает группу доступности Always On SQL Server в кластере Kubernetes с тремя репликами. Вторичные реплики находятся в режиме синхронной фиксации.

В Kubernetes развертывание включает оператор SQL Server, контейнеры SQL Server и службы балансировщика нагрузки. Оператор автоматически управляет группой доступности. В статье описывается выполнение следующих задач:

- Развертывание оператора, контейнеров SQL Server и служб балансировки нагрузки.
- Подключение к группе доступности с помощью служб.
- Добавление базы данных в группу доступности.

## <a name="requirements"></a>Требования

- Кластер AKS Kubernetes с последней версией
- По крайней мере три узла
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Доступ к репозиторию GitHub [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)

> [!NOTE]
> Вы можете использовать любой тип кластера Kubernetes. Сведения о создании кластера Kubernetes в службе Azure Kubernetes (AKS) см. в статье [Создание кластера AKS](https://docs.microsoft.com/azure/aks/create-cluster).
>
> Используйте самую последнюю версию Kubernetes. Конкретная версия зависит от вашей подписки и региона. См. раздел [Поддерживаемые версии Kubernetes в AKS](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions).  
>
> Следующий скрипт создает кластер Kubernetes с четырьмя узлами в Azure. Перед его выполнением замените `<latest version>` на последнюю доступную версию. Например, `1.12.5`.
>
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version <latest version> --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Развертывание оператора, контейнеров SQL Server и служб балансировки нагрузки

1. Создайте [пространство имен](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

      В этом примере используется пространство имен `ag1`. Чтобы создать его, выполните следующую команду.
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      Все объекты, принадлежащие этому решению, находятся в пространстве имен `ag1`.

1. Настройте и разверните манифест оператора SQL Server.

      Скопируйте файл SQL Server [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) из репозитория [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      Файл `operator.yaml` является манифестом развертывания для оператора Kubernetes.
    
      Примените манифест к кластеру Kubernetes.
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Создайте секрет для Kubernetes с паролями для учетной записи `sa` и главным ключом экземпляра SQL Server.

      Создайте секрет с помощью `kubectl`.
      
      В следующем примере создается секрет `sql-secrets` в пространстве имен `ag1`. Секрет хранит два пароля:
      
      - `sapassword` хранит пароль для учетной записи `sa` SQL Server.
      - `masterkeypassword` хранит пароль, используемый для создания главного ключа SQL Server. 
    
   Скопируйте сценарий в терминал. Замените каждый `<>` сложным паролем и запустите сценарий, чтобы создать секрет.
    
   >[!NOTE]
   >Пароль не может использовать символы `&` или `` ` ``.
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. Разверните настраиваемый ресурс SQL Server.

      Скопируйте манифест SQL Server [`sqlserver.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) из репозитория [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      >[!NOTE]
      >Файл `sqlserver.yaml` описывает контейнеры SQL Server, утверждения постоянных томов, постоянные тома и службы балансировки нагрузки, необходимые для каждого экземпляра SQL Server.
    
      Примените манифест к кластеру Kubernetes.
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
На следующем рисунке показано успешное применение `kubectl apply` для этого примера.

![Создание контейнеров SQL Server](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

После применения манифеста SQL Server оператор развертывает контейнеры SQL Server.

Kubernetes помещает контейнеры в модули Pod. Используйте `kubectl get pods --namespace ag1` для просмотра состояния модулей Pod. На следующем рисунке показан пример состояния развертывания после развертывания модулей Pod с SQL Server. 

![Построенные модули](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Мониторинг развертывания

Для мониторинга развертывания можно использовать [панель мониторинга Kubernetes со службой Azure Kubernetes](https://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Используйте `az aks browse` для запуска панели мониторинга. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Подключение к группе доступности с помощью служб

В примере [`ag-services.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) описываются службы балансировки нагрузки, которые могут подключаться к репликам группы доступности. 

- `ag1-primary` предоставляет конечную точку для подключения к первичной реплике.
- `ag1-secondary` предоставляет конечную точку для подключения к любой вторичной реплике.

При применении файла манифеста Kubernetes создает службы балансировки нагрузки для каждого типа реплики. Служба балансировки нагрузки включает IP-адрес. Используйте его для подключения к нужному типу реплики.

Чтобы развернуть службы, выполните следующую команду.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

После развертывания служб используйте `kubectl get services --namespace ag1` для получения IP-адреса служб.

С помощью IP-адреса можно подключиться к экземпляру SQL Server, где размещается каждый тип реплики.

На следующем рисунке показаны:

- Выходные данные `kubectl get services` для пространства имен `ag1`.

- Службы балансировки нагрузки, создаваемые для каждого контейнера SQL Server. Используйте эти IP-адреса в качестве конечных точек для прямого подключения к экземплярам SQL Server в кластере.

- Подключение `sqlcmd` к первичной реплике с учетной записью `sa` через конечную точку балансировщика нагрузки.

![Подключение](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных в группу доступности

>[!NOTE]
>Сейчас SQL Server Management Studio не позволяет добавить базу данных в группу доступности. Используйте для этого Transact-SQL.

После того как Kubernetes создаст контейнер SQL Server, выполните следующие действия, чтобы добавить базу данных в группу доступности.

1. [Подключитесь](sql-server-linux-kubernetes-connect.md) к экземпляру SQL Server в кластере.

1. Создание базы данных.

      ```sql
      CREATE DATABASE [demodb]
      ```

1. Создайте полную резервную копию базы данных, чтобы начать цепочку журналов.

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. Добавьте базу данных в группу доступности.

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
Группа доступности создается с автоматическим заполнением, поэтому SQL Server автоматически создаст вторичные реплики.

Состояние группы доступности можно просмотреть на панели мониторинга группы доступности SQL Server Management Studio.

![панель мониторинга](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Следующие шаги

- [Подключение к группе доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-connect.md)

- [Управление группой доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-manage.md)

- [SQL Server поддерживает группы доступности в контейнерах в кластере Kubernetes](sql-server-ag-kubernetes.md)
