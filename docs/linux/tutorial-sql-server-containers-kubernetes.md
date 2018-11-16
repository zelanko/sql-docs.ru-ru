---
title: Развертывание контейнера SQL Server в Kubernetes с помощью службы Azure Kubernetes (AKS) | Документация Майкрософт
description: Этом руководстве показано, как развернуть решение высокой доступности SQL Server с помощью Kubernetes в службе Azure Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: sql-linux,mvc
ms.technology: linux
ms.openlocfilehash: 1053f3a11bed9efbf75d7270f677c9f226221a3f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674204"
---
# <a name="deploy-a-sql-server-container-in-kubernetes-with-azure-kubernetes-services-aks"></a>Развертывание контейнера SQL Server в Kubernetes с помощью службы Azure Kubernetes (AKS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Узнайте, как настроить экземпляр SQL Server на платформе Kubernetes в службе Kubernetes Azure (AKS) в постоянное хранилище для обеспечения высокой доступности (HA). Решение обеспечивает устойчивость. Экземпляр SQL Server в случае сбоя Kubernetes автоматически повторно создает ее в новый модуль. Kubernetes предоставляет также устойчивость к сбоям узла.

Этот учебник демонстрирует настройку высокой доступности экземпляра SQL Server в контейнере в AKS. Вы также можете создать [группы доступности AlwaysOn для SQL Server контейнеров](sql-server-ag-kubernetes.md). Чтобы сравнить две различные решения Kubernetes, см. в разделе [высокий уровень доступности для SQL Server контейнеров](sql-server-linux-container-ha-overview.md).

> [!div class="checklist"]
> * Создать пароль SA
> * Создание хранилища
> * Создать развертывание
> * Подключение с помощью SQL Server Management Studio (SSMS)
> * Проверка восстановления

## <a name="ha-solution-on-kubernetes-running-in-azure-kubernetes-service"></a>Решения высокой ДОСТУПНОСТИ на платформе Kubernetes, запущенные в службе Azure Kubernetes

Kubernetes 1.6 и более поздних версий имеется поддержка [классы хранения](https://kubernetes.io/docs/concepts/storage/storage-classes/), [утверждения постоянного тома](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)и [тип тома дисков Azure](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). Можно создать и управлять экземплярами SQL Server непосредственно на платформе Kubernetes. Пример в этой статье показано, как создать [развертывания](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) для достижения высокого уровня доступности конфигурации, аналогичную экземпляра отказоустойчивого кластера общий диск. В этой конфигурации Kubernetes играет роль оркестратора кластера. При сбое экземпляру SQL Server в контейнере, orchestrator обеспечивает начальную загрузку другой экземпляр контейнера, который подключается к тем же постоянное хранилище.

![Схема кластера Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — это контейнер в [pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Kubernetes управляет ресурсами кластера. Объект [реплика](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует, что модуль автоматическое восстановление после сбоя узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, на котором размещена IP-адресом, которое изменяется после выхода из строя `mssql-server`.

На следующей схеме `mssql-server` сбой контейнер. Как orchestrator Kubernetes гарантирует правильное количество работоспособных экземпляров в реплике задать и запускает контейнер в соответствии с конфигурацией. Оркестратор начинает новый pod на одном узле, и `mssql-server` повторно подключается к тем же постоянное хранилище. Служба подключается к создан повторно `mssql-server`.

![Схема кластера Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

На следующей схеме для узла, на котором размещается `mssql-server` сбой контейнер. Оркестратор начинает новый pod на другом узле, и `mssql-server` повторно подключается к тем же постоянное хранилище. Служба подключается к создан повторно `mssql-server`.

![Схема кластера Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

## <a name="prerequisites"></a>предварительные требования

* **Кластер Kubernetes**
   - Руководства требуется кластер Kubernetes. В действиях используется [kubectl](https://kubernetes.io/docs/user-guide/kubectl/) для управления кластером. 

   - См. в разделе [развертывание кластера службы контейнеров Azure (AKS)](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster) для создания и подключения к кластеру Kubernetes в AKS при помощи одного узла `kubectl`. 

   >[!NOTE]
   >Для защиты от сбоя узла, кластер Kubernetes требует более чем на одном узле.

* **Azure CLI 2.0.23**
   - Инструкции в этом руководстве проверялись с использованием Azure CLI 2.0.23.

## <a name="create-an-sa-password"></a>Создать пароль SA

Создайте пароль SA в кластере Kubernetes. Kubernetes можно управлять сведения конфиденциальные данные, такие как пароли, как [секреты](https://kubernetes.io/docs/concepts/configuration/secret/).

Следующая команда создает пароль для учетной записи SA:

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   Замените `MyC0m9l&xP@ssw0rd` сложный пароль.

   Чтобы создать секрет в Kubernetes с именем `mssql` , содержащий значение `MyC0m9l&xP@ssw0rd` для `SA_PASSWORD`, выполните команду.


## <a name="create-storage"></a>Создание хранилища

Настройка [постоянного тома](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) и [утверждение постоянного тома](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection) в кластере Kubernetes. Выполните следующие действия: 

1. Создайте манифест для определения класса хранения и постоянного тома утверждения.  Манифест задает средство подготовки хранилища, параметры, и [освободить политики](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming). Кластер Kubernetes этот манифест используется для создания постоянного хранилища. 

   В следующем примере yaml определяет класс хранения и утверждение постоянного тома. Средство подготовки класс хранения является `azure-disk`, поскольку в этом кластере Kubernetes в Azure. Тип учетной записи хранения `Standard_LRS`. Утверждение постоянного тома называется `mssql-data`. Включает в себя метаданные утверждение постоянного тома заметки подключении его обратно в класс хранения. 

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

1. Создание утверждения постоянного тома в Kubernetes.

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   `<Path to pvc.yaml file>` — Это расположение, где был сохранен файл.

   Постоянный том автоматически создается как учетная запись хранилища Azure и привязан к утверждение постоянного тома. 

    ![Снимок экрана: команда утверждение постоянного тома](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. Проверьте утверждение постоянного тома.

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   `<PersistentVolumeClaim>` Это имя утверждения постоянного тома.

   На предыдущем шаге, с именем утверждение постоянного тома `mssql-data`. Чтобы просмотреть метаданные о утверждение постоянного тома, выполните следующую команду:

   ```azurecli
   kubectl describe pvc mssql-data
   ```

   Возвращенные метаданные включает значение с именем `Volume`. Это значение сопоставляется с именем большого двоичного объекта.

   ![Снимок экрана: Возвращенные метаданные, включая тома](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

   Значение для тома соответствующую часть имени большого двоичного объекта на портале Azure следующим образом: 

   ![Снимок экрана Azure имя портала большого двоичного объекта](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. Проверьте постоянного тома.

   ```azurecli
   kubectl describe pv
   ```

   `kubectl` Возвращает метаданные о постоянного тома, который был автоматически создан и привязан к утверждение постоянного тома. 

## <a name="create-the-deployment"></a>Создать развертывание

В этом примере экземпляр SQL Server для размещения контейнеров описан как объект развертывания Kubernetes. В результате развертывания создается набор реплик. Реплика создается pod. 

На этом шаге создайте манифест для описания контейнера на основе SQL Server [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) образа Docker. Манифеста ссылки `mssql-server` утверждение постоянного тома и `mssql` секрет, который вы уже применили к кластеру Kubernetes. В манифесте также описывается [службы](https://kubernetes.io/docs/concepts/services-networking/service/). Эта служба — это балансировщик нагрузки. Подсистема балансировки нагрузки гарантирует, что IP-адрес сохраняется после восстановления экземпляра SQL Server. 

1. Создайте манифест (yaml-файл) для описания развертывания. В следующем примере описывается развертывание, включая контейнер, основанный на образ контейнера SQL Server.

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
           image: mcr.microsoft.com/mssql/server/mssql-server-linux
           ports:
           - containerPort: 1433
           env:
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

   Скопируйте приведенный выше код в новый файл с именем `sqldeployment.yaml`. Обновите следующие значения: 

   * `value: "Developer"`: Задает контейнер для запуска SQL Server Developer edition. Выпуск Developer edition не лицензирован для производственных данных. Если для использования в рабочей среде развертывания, задайте соответствующий выпуск (`Enterprise`, `Standard`, или `Express`). 

      >[!NOTE]
      >Дополнительные сведения см. в разделе [как лицензии SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

   * `persistentVolumeClaim`— Это значение требуется запись для `claimName:` , сопоставляется с именем, используется для утверждения постоянного тома. В этом руководстве используется `mssql-data`. 

   * `name: SA_PASSWORD`: Настраивает образ контейнера, чтобы задать пароль системного Администратора, как определено в этом разделе.

     ```yaml
     valueFrom:
       secretKeyRef:
         name: mssql
         key: SA_PASSWORD 
     ```

     Когда Kubernetes развертывает контейнер, он ссылается на секрет с именем `mssql` для получения значения пароля. 

   >[!NOTE]
   >С помощью `LoadBalancer` тип службы, экземпляр SQL Server доступен удаленно (через Интернет) через порт 1433.

   Сохраните файл (например, **sqldeployment.yaml**).

1. Создайте развертывание.

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   `<Path to sqldeployment.yaml file>` — Это расположение, где был сохранен файл.

   ![Снимок экрана: команда развертывания](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   Создаются развертывания и обслуживания. Экземпляр SQL Server находится в контейнере, подключенных в постоянное хранилище.

   Чтобы просмотреть состояние модуля, введите `kubectl get pod`.

   ![Снимок экрана: Команда get pod](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   На предыдущем рисунке, модуль находится в состоянии `Running`. Это состояние указывает, что контейнер готов. Это может занять несколько минут.

   >[!NOTE]
   >После создания развертывания может занять несколько минут, прежде чем модуль является видимым. Задержка — это, так как кластер извлекает [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) образ из Docker hub. После первой будет отображен образ, последующие развертывания могут выполняться быстрее, если развертывание на узел, который уже содержит изображения, кэшированные на нем. 

1. Убедитесь, что они работают. Выполните следующую команду:

   ```azurecli
   kubectl get services 
   ```

   Эта команда возвращает только выполняющимися службами, а также внутренние и внешние IP-адреса для служб. Обратите внимание, внешний IP-адрес для `mssql-deployment` службы. Используйте этот IP-адрес для подключения к SQL Server. 

   ![Снимок экрана: Команда get-service](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Дополнительные сведения о состоянии объектов в кластере Kubernetes выполните следующую команду:

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>Подключитесь к экземпляру SQL Server

Если вы настроили контейнер, как описано, можно подключить к приложению извне виртуальной сети Azure. Используйте `sa` учетной записи и внешних IP-адресов для службы. Используйте пароль, который вы настроили в качестве секрета Kubernetes. 

Следующие приложения можно использовать для подключения к экземпляру SQL Server. 

* [SSMS](https://docs.microsoft.com/sql/linux/sql-server-linux-manage-ssms)

* [SSDT](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssdt)

* sqlcmd
   
   Для подключения с `sqlcmd`, выполните следующую команду:

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   Замените следующие значения:
      
    - `<External IP Address>` IP-адресом для `mssql-deployment` службы 
    - `MyC0m9l&xP@ssw0rd` с помощью пароля

## <a name="verify-failure-and-recovery"></a>Проверка восстановления

Чтобы проверить, восстановления, можно удалить модуль. Выполните следующие действия:

1. Список модулей pod SQL Server.

   ```azurecli
   kubectl get pods
   ```

   Запомните имя pod под управлением SQL Server.

1. Удалите модуль.

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0` значение, возвращаемое из предыдущий шаг для имя модуля. 

Kubernetes автоматически повторно создает pod для восстановления экземпляра SQL Server и подключения в постоянное хранилище. Используйте `kubectl get pods` чтобы убедиться, что развертывается новый pod. Используйте `kubectl get services` для убедитесь, что IP-адрес для нового контейнера. 

## <a name="summary"></a>Сводка

В этом руководстве вы узнали, как развернуть контейнеры SQL Server в кластер Kubernetes для обеспечения высокой доступности. 

> [!div class="checklist"]
> * Создать пароль SA
> * Создание хранилища
> * Создать развертывание
> * Подключение с помощью SQL Server Management Studios (SSMS)
> * Проверка восстановления

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
>[Общие сведения о Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)


