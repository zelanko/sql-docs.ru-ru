---
title: Развертывание контейнера SQL Server с помощью служб Azure Kubernetes (AKS)
description: В этом руководстве показано, как развернуть решение высокой доступности SQL Server с помощью Kubernetes в службе Azure Kubernetes.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 729aacf69f8aa36964f33c0bcb282351a67ab444
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635433"
---
# <a name="deploy-a-sql-server-container-in-kubernetes-with-azure-kubernetes-services-aks"></a>Развертывание контейнера SQL Server в Kubernetes с помощью служб Azure Kubernetes (AKS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Узнайте, как настроить экземпляр SQL Server в Kubernetes в службе Azure Kubernetes (AKS) с постоянным хранилищем для обеспечения высокой доступности (HA). Такое решение обеспечивает устойчивость. Если экземпляр SQL Server терпит сбой, Kubernetes автоматически повторно создает его в новом модуле Pod. Kubernetes также обеспечивает устойчивость к сбою узла.

В этом руководстве показано, как настроить высокодоступный экземпляр SQL Server в контейнере в AKS.

> [!div class="checklist"]
> * Создание пароля SA
> * Создание хранилища
> * Создание развертывания
> * Подключение в SQL Server Management Studio (SSMS)
> * Проверка сбоя и восстановление

## <a name="ha-solution-on-kubernetes-running-in-azure-kubernetes-service"></a>Решение высокой доступности в Kubernetes, работающее в службе Azure Kubernetes

В Kubernetes версии 1.6 и более поздних поддерживаются [классы хранилища](https://kubernetes.io/docs/concepts/storage/storage-classes/), [утверждения постоянного тома](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims), а также [тип тома диска Azure](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). Поддерживается создание собственных экземпляров SQL Server в собственном коде Kubernetes и управление ими. В примере, приведенном в этой статье, показано, как создать [развертывание](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) для достижения высокой доступности, аналогичной экземпляру отказоустойчивого кластера общего диска. В этой конфигурации Kubernetes играет роль оркестратора кластера. При сбое экземпляра SQL Server в контейнере оркестратор загружает другой экземпляр контейнера, который подключается к тому же постоянному хранилищу.

![Схема кластера Kubernetes с SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — это контейнер внутри модуля [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Kubernetes управляет ресурсами в кластере. Применение [набора реплик](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует автоматическое восстановление pod в случае отказа узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, которая содержит IP-адрес, остающийся неизменным в случае отказа `mssql-server`.

На следующей схеме в контейнере `mssql-server` происходит сбой. Как оркестратор Kubernetes гарантирует правильное количество работоспособных экземпляров в наборе реплик и запускает новый контейнер в соответствии с конфигурацией. Оркестратор запускает новый модуль Pod на том же узле, и `mssql-server` повторно подключается к тому же постоянному хранилищу. Служба подключается к повторно созданному `mssql-server`.

![Схема кластера Kubernetes с SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

На следующей схеме сбой затронул узел, на котором размещен контейнер `mssql-server`. Оркестратор запускает новый модуль Pod на другом узле, и `mssql-server` повторно подключается к тому же постоянному хранилищу. Служба подключается к повторно созданному `mssql-server`.

![Схема кластера Kubernetes с SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

## <a name="prerequisites"></a>Предварительные требования

* **Кластер Kubernetes**
   - Для работы с этим руководством требуется кластер Kubernetes. В шагах для управления кластером используется [kubectl](https://kubernetes.io/docs/user-guide/kubectl/). 

   - См. раздел [Развертывание кластера службы Azure Kubernetes (AKS)](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster) для создания кластера Kubernetes с одним узлом в AKS с помощью `kubectl`. 

   >[!NOTE]
   >Для защиты от сбоя узла кластер Kubernetes требует наличия нескольких узлов.

* **Azure CLI 2.0.23**
   - Инструкции в этом руководстве проверены на соответствие Azure CLI 2.0.23.

## <a name="create-an-sa-password"></a>Создание пароля SA

Создайте пароль SA в кластере Kubernetes. Kubernetes может управлять конфиденциальными сведениями о конфигурации, например паролями, в качестве [секретов](https://kubernetes.io/docs/concepts/configuration/secret/).

Следующая команда создает пароль для учетной записи SA:

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   Замените `MyC0m9l&xP@ssw0rd` надежным паролем.

   Чтобы создать в Kubernetes секрет с именем `mssql`, который содержит значение `MyC0m9l&xP@ssw0rd` для `SA_PASSWORD`, выполните команду.


## <a name="create-storage"></a>Создание хранилища

Настройте [постоянный том](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) и [утверждение постоянного тома](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection) в кластере Kubernetes. Необходимо выполнить следующие шаги. 

1. Создайте манифест, чтобы определить класс хранения и утверждение постоянного тома.  В манифесте описана подготовка хранилища, параметры и [политика обработки заявок на хранение](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming). Кластер Kubernetes использует этот манифест для создания постоянного хранилища. 

   В следующем примере на языке YAML определяется класс хранения и утверждение постоянного тома. Подготовка класса хранилища — `azure-disk`, так как этот кластер Kubernetes находится в Azure. Тип учетной записи хранения — `Standard_LRS`. Утверждение постоянного тома называется `mssql-data`. Метаданные утверждения постоянного тома содержат заметку, которая относит его к классу хранения. 

   ```yaml
   kind: StorageClass
   apiVersion: storage.k8s.io/v1beta1
   metadata:
        name: azure-disk
   provisioner: kubernetes.io/azure-disk
   parameters:
     storageaccounttype: Standard_LRS
     kind: Managed
   ---
   kind: PersistentVolumeClaim
   apiVersion: v1
   metadata:
     name: mssql-data
     annotations:
       volume.beta.kubernetes.io/storage-class: azure-disk
   spec:
     accessModes:
     - ReadWriteOnce
     resources:
       requests:
         storage: 8Gi
   ```

   Сохраните файл (например, **pvc.yaml**).

1. Создайте утверждение постоянного тома в Kubernetes.

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   `<Path to pvc.yaml file>` — это расположение, в котором сохранен файл.

   Постоянный том создается автоматически как учетная запись хранения Azure и связывается с утверждением постоянного тома. 

    ![Снимок экрана: команда утверждения постоянного тома](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. Проверьте утверждение постоянного тома.

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   Утверждение постоянного тома теперь называется `<PersistentVolumeClaim>`.

   На предыдущем шаге утверждение постоянного тома называется `mssql-data`. Чтобы просмотреть метаданные об утверждении постоянного тома, выполните следующую команду:

   ```azurecli
   kubectl describe pvc mssql-data
   ```

   Возвращаемые метаданные содержат значение с именем `Volume`. Это значение сопоставляется с именем большого двоичного объекта.

   ![Снимок экрана возвращенных метаданных, включающих том](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

   Значение тома соответствует части имени большого двоичного объекта на следующем снимке экрана портала Azure: 

   ![Снимок экрана: имя большого двоичного объекта на портале Azure](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. Проверьте постоянный том.

   ```azurecli
   kubectl describe pv
   ```

   `kubectl` возвращает метаданные постоянного тома, который создается автоматически и связывается с утверждением постоянного тома. 

## <a name="create-the-deployment"></a>Создание развертывания

В этом примере контейнер, в котором размещен экземпляр SQL Server, описан как объект развертывания Kubernetes. При развертывании создается набор реплик. Набор реплик создает Pod. 

На этом шаге создайте манифест, описывающий контейнер на основе образа SQL Server [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) в Docker. Манифест ссылается на утверждение постоянного тома `mssql-server` и секрет `mssql`, который вы уже применили к кластеру Kubernetes. Манифест также описывает [службу](https://kubernetes.io/docs/concepts/services-networking/service/). Эта служба является подсистемой балансировки нагрузки. Она гарантирует, что IP-адрес будет сохранен после восстановления экземпляра SQL Server. 

1. Создайте манифест (YAML-файл) для описания развертывания. В следующем примере описывается развертывание, включая контейнер, основанный на образе контейнера SQL Server.

   ```yaml
   apiVersion: apps/v1beta1
   kind: Deployment
   metadata:
     name: mssql-deployment
   spec:
     replicas: 1
     template:
       metadata:
         labels:
           app: mssql
       spec:
         terminationGracePeriodSeconds: 10
         containers:
         - name: mssql
           image: mcr.microsoft.com/mssql/server:2017-latest
           ports:
           - containerPort: 1433
           env:
           - name: MSSQL_PID
             value: "Developer"
           - name: ACCEPT_EULA
             value: "Y"
           - name: SA_PASSWORD
             valueFrom:
               secretKeyRef:
                 name: mssql
                 key: SA_PASSWORD 
           volumeMounts:
           - name: mssqldb
             mountPath: /var/opt/mssql
         volumes:
         - name: mssqldb
           persistentVolumeClaim:
             claimName: mssql-data
   ---
   apiVersion: v1
   kind: Service
   metadata:
     name: mssql-deployment
   spec:
     selector:
       app: mssql
     ports:
       - protocol: TCP
         port: 1433
         targetPort: 1433
     type: LoadBalancer
   ```

   Скопируйте приведенный выше код в новый файл с именем `sqldeployment.yaml`. Измените следующие значения: 

   * MSSQL_PID `value: "Developer"`: задает контейнер для запуска SQL Server Developer Edition. Выпуск Developer Edition не лицензирован для рабочих данных. Если развертывание предназначено для использования в рабочей среде, задайте соответствующий выпуск`Enterprise` (`Standard` или `Express`). 

      >[!NOTE]
      >Дополнительные сведения см. в статье о [лицензировании SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

   * `persistentVolumeClaim`: Это значение требует наличия записи для `claimName:`, сопоставленного с именем, используемым для утверждения постоянного тома. В этом учебнике используется `mssql-data`. 

   * `name: SA_PASSWORD`: настраивает образ контейнера для установки пароля SA, определенного в этом разделе.

     ```yaml
     valueFrom:
       secretKeyRef:
         name: mssql
         key: SA_PASSWORD 
     ```

     Когда Kubernetes развертывает контейнер, он обращается к секрету с именем `mssql`, чтобы получить значение пароля. 

   >[!NOTE]
   >Используя тип службы `LoadBalancer`, экземпляр SQL Server будет доступен удаленно (через Интернет) через порт 1433.

   Сохраните файл (например, **sqldeployment.yaml**).

1. Создайте развертывание.

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   `<Path to sqldeployment.yaml file>` — это расположение, в котором сохранен файл.

   ![Снимок экрана команды развертывания](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   Развертывание и служба будут созданы. Экземпляр SQL Server находится в контейнере, подключенном к постоянному хранилищу.

   Для просмотра состояния модуля Pod введите `kubectl get pod`.

   ![Снимок экрана команды get pod](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   На предыдущем изображении модуль имеет состояние `Running`. Это состояние указывает, что контейнер готов. Это может занять несколько минут.

   >[!NOTE]
   >После создания развертывания может пройти несколько минут, прежде чем будет виден модуль. Задержка связана с тем, что кластер извлекает образ [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) из центра Docker. После первого извлечения образа последующие развертывания могут выполняться быстрее, если развертывание выполняется на узле, где уже есть кэшированный образ. 

1. Убедитесь в том, что службы запущены. Выполните следующую команду:

   ```azurecli
   kubectl get services 
   ```

   Эта команда возвращает службы, которые выполняются, а также внутренние и внешние IP-адреса этих служб. Запишите внешний IP-адрес для службы `mssql-deployment`. Используйте этот IP-адрес для подключения к SQL Server. 

   ![Снимок экрана команды get service](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Чтобы получить дополнительные сведения о состоянии объектов в кластере Kubernetes, выполните команду:

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>Подключение к экземпляру SQL Server

Если вы настроили контейнер согласно описанию, вы можете подключиться к приложению извне виртуальной сети Azure. Используйте учетную запись `sa` и внешний IP-адрес для службы. Используйте пароль, настроенный в качестве секрета Kubernetes. 

Затем можно использовать следующие приложения для подключения к экземпляру SQL Server. 

* [SSMS](https://docs.microsoft.com/sql/linux/sql-server-linux-manage-ssms)

* [SSDT](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssdt)

* sqlcmd
   
   Чтобы подключиться через `sqlcmd`, используйте следующую команду:

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   Измените следующие значения:
      
    - `<External IP Address>` — на IP-адрес службы `mssql-deployment`. 
    - `MyC0m9l&xP@ssw0rd` — на свой пароль.

## <a name="verify-failure-and-recovery"></a>Проверка сбоя и восстановление

Чтобы проверить сбой и восстановление, можно удалить модуль Pod. Выполните следующие шаги:

1. Выведите список модулей Pod, где работает SQL Server.

   ```azurecli
   kubectl get pods
   ```

   Запишите имя модуля, на котором работает SQL Server.

1. Удалите модуль.

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0` — это значение, возвращенное на предыдущем шаге для имени Pod. 

Kubernetes автоматически повторно создает Pod для восстановления экземпляра SQL Server и подключения к постоянному хранилищу. Используйте `kubectl get pods` для проверки развертывания нового Pod. Используйте `kubectl get services` для проверки того, что IP-адрес контейнера не изменился. 

## <a name="summary"></a>Сводка

В этом руководстве вы узнали, как развертывать контейнеры SQL Server в кластере Kubernetes для обеспечения высокой доступности. 

> [!div class="checklist"]
> * Создание пароля SA
> * Создание хранилища
> * Создание развертывания
> * Подключение в SQL Server Management Studio (SSMS)
> * Проверка сбоя и восстановление

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
>[Введение в Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)


