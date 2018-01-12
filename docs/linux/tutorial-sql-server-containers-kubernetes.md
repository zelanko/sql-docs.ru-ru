---
title: "Настройка высокой доступности SQL Server контейнер в Kubernetes | Документы Microsoft"
description: "Этого учебника показано, как развернуть решение высокого уровня доступности SQL Server с Kubernetes в службе контейнера Azure."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: mvc
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 5055a5956ce83dadae3cef13f0855db02a61d01b
ms.sourcegitcommit: 06131936f725a49c1364bfcc2fccac844d20ee4d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="configure-sql-server-container-in-kubernetes-for-high-availability"></a>Настройка SQL Server контейнер в Kubernetes для обеспечения высокой доступности

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Следуйте этой статьи, чтобы настроить экземпляр SQL Server на Kubernetes контейнера службы Azure (AKS) постоянного хранилища для обеспечения высокой доступности. Это решение предоставляет устойчивости. Если экземпляр SQL Server завершается ошибкой, Kubernetes автоматически повторно создает ее в новый модуль. AKS обеспечивает устойчивость к сбоям Kubernetes узла. 

Этом учебнике показано, как настроить экземпляр SQL Server высокой доступности в контейнерах, с помощью AKS. 

> [!div class="checklist"]
> * Пароль системного Администратора создать
> * Создание хранилища
> * Создание развертывания
> * Подключение с входящим управления SQL Server (среда SSMS)
> * Проверка восстановления

### <a name="ha-solution-using-kubernetes-running-in-azure-container-service"></a>Решения высокой ДОСТУПНОСТИ с помощью Kubernetes, запущенные в службе контейнера Azure

Kubernetes 1.6 + реализована поддержка [классы хранения](http://kubernetes.io/docs/concepts/storage/storage-classes/), [постоянные тома утверждений](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)и [драйвер тома диска Azure](http://github.com/Azure/azurefile-dockervolumedriver). Можно создавать и управлять экземплярами SQL Server непосредственно в Kubernetes. Пример в этой статье показано, как создать [развертывания](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) для достижения высокого уровня доступности конфигурации, аналогично отказоустойчивый кластер общего диска. В этой конфигурации Kubernetes играет роль orchestrator кластера. В случае сбоя экземпляра SQL Server в контейнере orchestrator загружает другой экземпляр контейнера, который присоединяет же постоянное хранилище.

![Кластер Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — контейнер [pod](http://kubernetes.io/docs/concepts/workloads/pods/pod/). Kubernetes организует ресурсы в кластере. Объект [реплика](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует, что pod автоматическое восстановление после сбоя узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, на котором размещена IP-адреса, остаются теми же после выхода из строя `mssql-server`.

На следующей диаграмме `mssql-server` сбой контейнер. Как orchestrator Kubernetes гарантирует правильное число исправных экземпляров в реплике задать и начинает новый контейнер, в соответствии с конфигурацией. Orchestrator запускает новый pod на том же узле и `mssql-server` повторно подключается к же постоянное хранилище. Служба подключается к вновь созданной `mssql-server`.

![Кластер Kubernetes SQL Server после](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

На следующей диаграмме для узла, на котором размещается `mssql-server` сбой контейнер. Orchestrator запускает новый pod на разных узлах и `mssql-server` повторно подключается к же постоянное хранилище. Служба подключается к вновь созданной `mssql-server`.

![Кластер Kubernetes SQL Server после](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

## <a name="prerequisites"></a>предварительные требования

* **Kubernetes кластера**
   - Учебник по требуется кластер Kubernetes. Используйте шаги [kubectl](https://kubernetes.io/docs/user-guide/kubectl/), для управления кластером. 

   - Инструкции по [развертывание кластера службы контейнера Azure (AKS)](http://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster) для создания и подключения к Kubernetes кластер с одним узлом в AKS с `kubectl`. 

   >[!NOTE]
   >Для защиты от сбоев узлов кластера Kubernetes требует более чем одним узлом.

* **Azure CLI 2.0.23**
   - Инструкции в этом учебнике были проверены для Azure CLI 2.0.23.

## <a name="create-sa-password"></a>Пароль системного Администратора создать

Создайте пароль SA Kubernetes кластера. Kubernetes можно управлять конфигурации конфиденциальные сведения, такие как пароли, как [секреты](http://kubernetes.io/docs/concepts/configuration/secret/).

Следующая команда создает пароль для учетной записи SA:

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   Замените `MyC0m9l&xP@ssw0rd` с сложный пароль.

   Создание секрета в Kubernetes с именем `mssql` , содержащий значение `MyC0m9l&xP@ssw0rd` для `SA_PASSWORD`, выполните команду.


## <a name="create-storage"></a>Создание хранилища

Настройка [постоянные тома](http://kubernetes.io/docs/concepts/storage/persistent-volumes/), и [утверждения постоянные тома](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection) Kubernetes кластера. Выполните следующие действия: 

1. Создание манифеста задать класс хранения и постоянные тома утверждения.  Манифест задает средство подготовки хранилища, параметры и [освободить политики](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming). Кластер Kubernetes использует этот манифест для создания постоянного хранилища. 

   В следующем примере yaml определяет класс хранения и постоянные тома утверждения. Средство подготовки класса хранения является `azure-disk` так, как это Kubernetes кластер находится в Azure. Тип учетной записи хранилища `Standard_LRS`. Утверждение постоянные тома называется `mssql-data`. Постоянные тома утверждения метаданные включают в себя заметки подключение его обратно в класс хранения. 

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

   Сохраните файл, например **pvc.yaml**.

1. Создайте постоянные тома утверждение Kubernetes.

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   * `<Path to pvc.yaml file>`
      * Расположение, где был сохранен файл.

   Постоянные тома автоматически создается как учетная запись хранилища Azure и связанный с утверждением постоянные тома. 

    ![Команда утверждения постоянные тома](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. Проверка утверждения постоянные тома.

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   * `<PersistentVolumeClaim>`
      * Имя утверждения постоянные тома.

    В предыдущем шаге, с именем утверждения постоянные тома `mssql-data`. Чтобы просмотреть метаданные о утверждения постоянные тома, выполните следующую команду:

    ```azurecli
    kubectl describe pvc mssql-data
    ```

    Возвращенные метаданные включает значение с именем `Volume`. Это значение сопоставляется с именем большого двоичного объекта.

    ![Описываются тома](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

    Значение для тома, совпадения в имени большого двоичного объекта на следующем рисунке с портала Azure: 

    ![Описания корпоративного портала](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. Проверьте, постоянно тома.

   ```azurecli
   kubectl describe pv
   ```

   `kubectl`Возвращает метаданные о постоянных том, который был автоматически создаются и связываются с утверждением постоянные тома. 

## <a name="create-the-deployment"></a>Создание развертывания

В этом примере описывается контейнер, где установлен экземпляр SQL Server как объект Kubernetes развертывания. В результате развертывания создается набор реплик. Реплика создается pod. 

На этом шаге, создайте манифест для описания контейнер, основанный на Microsoft SQL Server [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) образа Docker. Манифест ссылается `mssql-server` утверждения постоянные тома и `mssql` секрет уже применены к Kubernetes кластера. Также этот манифест описывает [службы](http://kubernetes.io/docs/concepts/services-networking/service/). Эта служба является подсистемой балансировки нагрузки. Подсистема балансировки нагрузки гарантирует, что IP-адрес сохраняется после восстановления экземпляра SQL Server. 

1. Создайте манифест - файл yaml - для описания развертывания. В следующем примере описывается развертывание, включая контейнера на основе образа контейнера SQL Server.

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
           image: microsoft/mssql-server-linux
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

   * `value: "Developer"`
     * Задает контейнер для запуска SQL Server Developer edition. Выпуск Developer edition не лицензирован для производственных данных. Если для использования в рабочей среде развертывания, установите соответствующий выпуск. Может принимать одно из `Enterprise`, `Standard`, или `Express`. 

      >[!NOTE]
      >Дополнительные сведения см. в разделе [как лицензии SQL Server](http://www.microsoft.com/sql-server/sql-server-2017-pricing).

   * `persistentVolumeClaim`
     * Это значение требуется для записи `claimName:` , сопоставляет имя, используемое для утверждения постоянные тома. В этой статье используется `mssql-data`. 

   * `name: SA_PASSWORD`
      * Настраивает образ контейнера, чтобы задать пароль SA, как определено в этом разделе.

      ```yaml
      valueFrom:
        secretKeyRef:
          name: mssql
          key: SA_PASSWORD 
      ```

       Когда Kubernetes развертывает контейнер, он ссылается на секрет с именем `mssql` необходимо получить значение для пароля. 

   >[!NOTE]
   >С помощью `LoadBalancer` тип службы, экземпляр SQL Server доступен удаленно (через Интернет) на порту 1433.

    Сохраните файл, например **sqldeployment.yaml**.

1. Создайте развертывание.

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   * `<Path to sqldeployment.yaml file>`
      * Расположение, где был сохранен файл.

   ![Команда развертывания](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   Создаются развертывания и обслуживания. Экземпляр SQL Server находится в контейнере - подключения в постоянное хранилище.

   Чтобы просмотреть состояние pod, введите `kubectl get pod`.

   ![Команда «получить» pod](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   >[!NOTE]
   >После создания развертывания может потребоваться несколько минут, прежде чем pod является видимым. Так как кластер должен запрашивать, задержка будет [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) образ из Docker hub. После его извлекается первый раз, последующие развертывания могут выполняться быстрее - при развертывании узла, который уже содержит изображение, кэшированные на нем. 

1. Убедитесь, что они работают. Выполните следующую команду:

   ```azurecli
   kubectl get services 
   ```

   Эта команда возвращает запущенных служб, а также внутренние и внешние IP-адресов для служб. Обратите внимание, внешний IP-адрес для `mssql-deployment` службы.  Используйте этот IP-адрес для подключения к SQL Server. 

   ![Команда «получить» службы](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Дополнительные сведения о состоянии объектов в кластере Kubernetes выполните следующую команду:

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>Подключитесь к экземпляру SQL Server

Если вы настроили контейнера, как описано, можно подключить к приложению за пределами виртуальной сети Azure. Используйте `sa` учетной записи и внешний IP-адрес для службы. Используйте пароль, который настроен как Kubernetes секрета. 

Следующие приложения можно использовать для подключения к экземпляру SQL Server. 

* [СРЕДА SSMS](http://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssms)

* [SSDT](http://docs.microsoft.com/en-us/sql/linux/sql-server-linux-develop-use-ssdt)

* SQLCMD, для подключения к `sqlcmd`, выполните следующую команду:

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   Замените следующие значения:
      - `<External IP Address>`IP-адрес для `mssql-deployment` службы 
      - `MyC0m9l&xP@ssw0rd`с помощью пароля

## <a name="verify-failure-and-recovery"></a>Проверка восстановления

Чтобы проверить восстановления можно удалить pod. Выполните следующие действия:

1. Список pod, на котором работает SQL Server.

   ```azurecli
   kubectl get pods
   ```

   Обратите внимание на имя типа pod, на котором работает SQL Server.

1. Удалите pod.

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0`значение, возвращаемое из предыдущий шаг для имени pod. 

Kubernetes автоматически восстанавливает pod для восстановления экземпляра SQL Server и подключения в постоянное хранилище. Используйте `kubectl get pods` чтобы убедиться, что развернут новый модуль. Используйте `kubectl get services` для убедитесь, что IP-адрес для нового контейнера. 

## <a name="summary"></a>Сводка

В этом учебнике вы узнали, как развернуть контейнеры SQL Server в кластер Kubernetes для обеспечения высокой доступности. 

> [!div class="checklist"]
> * Пароль системного Администратора создать
> * Создание хранилища
> * Создание развертывания
> * Подключение с входящим управления SQL Server (среда SSMS)
> * Проверка восстановления

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
>[Начальный - Kubernetes](http://docs.microsoft.com/en-us/azure/aks/intro-kubernetes)
