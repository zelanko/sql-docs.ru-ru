---
title: Настройка группы доступности SQL Server Always On в контейнерах Docker в Kubernetes | Документация Майкрософт
description: Этот учебник содержит описание развертывания SQL Server, группа доступности AlwaysOn с помощью Kubernetes в службе контейнеров Azure.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: sql-linux,mvc
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 119574498dec87bc38ab1b0904c53b7f62716427
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47665575"
---
# <a name="configure-a-sql-server-always-on-availability-group-on-docker-containers-in-kubernetes-with-azure-kubernetes-service-aks"></a>Настройка группы доступности SQL Server Always On в контейнерах Docker в Kubernetes со службой Azure Kubernetes (AKS)

Этот учебник демонстрирует настройку высокой доступности экземпляра SQL Server в контейнере в AKS. Вы также можете [развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md). Чтобы сравнить две различные решения Kubernetes, см. в разделе [высокий уровень доступности для SQL Server контейнеров](sql-server-linux-container-ha-overview.md).

В этом руководстве вы узнаете, как:  

> [!div class="checklist"]
> * Создание хранилища
> * Развертывание оператора SQL Server в кластере Kubernetes 
> * Создание секретов для Kubernetes
> * Развертывание экземпляров SQL Server и работоспособности агентов
> * Подключитесь к первичной реплике
> * Добавление базы данных в группу доступности

В этом учебнике показано архитектуры в [службы Azure Kubernetes (AKS)](http://docs.microsoft.com/azure/aks/). Если у вас нет подписки Azure, создайте [бесплатную учетную запись](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) перед началом работы.

На этой схеме представлено решение, в этом руководстве:

![кластер kubernetes — группы доступности](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

### <a name="deployment-methodology-for-kubernetes"></a>Методы развертывания для Kubernetes

Несколько действий, описанных в этой статье создайте манифест, а затем разверните манифест в кластер. Манифест — это yaml-файл с описанием развертываемых объектов Kubernetes.

Файлы .yaml в этом примере находятся в [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability).

Объекты содержат хранилища, операторы, модулей, контейнеров и служб.

## <a name="prerequisites"></a>предварительные требования

* Общие знания о этих технологий

  * [Kubernetes](http://kubernetes.io) версии 1.8
  * [Служба Azure Kubernetes (AKS)](http://docs.microsoft.com/azure/aks/)
  * [SQL Server в Docker](quickstart-install-connect-docker.md)
  * [SQL Server группы доступности AlwaysOn](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

* Кластер Kubernetes с четырьмя узлами.

  Инструкции см. [руководство: развертывание кластера службы Azure Kubernetes (AKS)](http://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster).

* Установка [ `kubectl` ](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster#install-the-kubectl-cli).

## <a name="configuration-and-deployment-procedures"></a>Процедуры настройки и развертывания

Учебник демонстрирует применение файлов .yaml к кластеру Kubernetes.

## <a name="create-the-secrets"></a>Создайте секреты

Чтобы создать Kubernetes секретов для хранения паролей для учетной записи SQL Server SA и главный ключ SQL Server, выполните следующую команду.

```azurecli
kubectl create secret generic sql-secrets --from-literal=sapassword="MyC0m9l&xP@ssw0rd" --from-literal=masterkeypassword="MyC0m9l&xP@ssw0rd2"
```

В рабочей среде используйте разные, сложный пароль.

## <a name="deploy-the-operator"></a>Развертывание оператора

Оператор Kubernetes развертывает экземпляры SQL Server и настраивает группы доступности в кластере Kubernetes. 

См. в статье на примере оператор [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml)

Скачайте `operator.yaml` из [образцы sql server](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/)

Разверните оператора как одна реплика развертывания Kubernetes.

Чтобы развернуть оператора:

Развертывание с помощью оператора `kubectl apply` команды.

```azurecli
kubectl apply -f operator.yaml
```

## <a name="create-the-sql-server-ag-deployment"></a>Создание развертывания групп Доступности SQL Server

Следующий шаг создает экземпляры SQL Server и группы доступности в одно развертывание Kubernetes. После применения этого развертывания в кластере, оператор развертываются экземпляры SQL Server как контейнеры Docker. Это развертывание приведет к три StatefulSets с один модуль. Каждая группа контейнеров pod будет включать два контейнера:

* Экземпляр SQL Server на основе `mssql-server` образа
* Контролер высокого уровня ДОСТУПНОСТИ

Кроме того развертывание описывает службу балансировки нагрузки для прослушивателя группы доступности

Чтобы развернуть mssql-server:

1. Копировать [sqlserver.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) к компьютеру.
2. Обновление `sqlserver.yaml` для вашей среды.


Чтобы развернуть экземпляры SQL Server и создайте группу доступности, выполните следующую команду.

```azurecli
kubectl apply -f sqlserver.yaml
```

## <a name="deploy-ag-services"></a>Развертывание группы Доступности служб

В кластере Kubernetes создайте службы подсистемы балансировки нагрузки, чтобы прямые вызовы к репликам в группе доступности.

[группы доступности services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) создает четыре службы.

* AG1-primary подключается к первичной реплике.
* AG1 получателя синхронизации подключается к синхронная вторичная реплика.
* AG1-получатель async подключается к асинхронной вторичной реплики.
* AG1-получатель config соединяется с репликой только для конфигурации. 

  >[!NOTE]
  >Эти службы подсистемы балансировки нагрузки приведены в качестве примеров. В этом руководстве не только для настройки реплики.


Развертывание служб балансировки нагрузки, что позволяет подключаться к группе доступности.

Для развертывания служб, выполните следующую команду.

```azurecli
kubectl apply -f ag-services.yaml
```

### <a name="monitor-the-deployment"></a>Мониторинг развертывания

Можно использовать [панели мониторинга Kubernetes со службой Azure Kubernetes (AKS)](https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard) мониторинге развертывания. 

Используйте `az aks browse` для запуска панели мониторинга. 

После развертывания могут обновляться только группы Доступности членство в списке и post-init сценарий T-SQL. Невозможно обновить другие свойства — ресурс должен быть удален и создан заново. Учетные данные для пользователей автоматически генерируемым можно менять с помощью `mssql-server-k8s-rotate-creds` задания.

## <a name="connect-to-the-sql-server-instance-hosting-the-primary-replica"></a>Подключитесь к экземпляру SQL Server, на котором размещена первичная реплика

`ag-services.yaml` Описывает имя службы Kubernetes `ag1-primary`. `ag1-primary` Создает балансировщик нагрузки Azure, выберите экземпляр SQL Server, на котором размещена первичная реплика. Использовать внешний IP-адрес службы, что целевой сервер, `sa` как учетную запись и пароль, созданный ранее в `mssql secret` пароля.

Используйте `kubectl get services` получить этот IP-адрес.

Пример:

![Пример службы получения](media\tutorial-sql-server-ag-containers-kubernetes\KubernetesGetServices.png)

На рисунке выше `ag1-primary` служба имеет внешний IP-адрес `104.42-50.138`. 

Чтобы подключиться к SQL Server с помощью проверки подлинности SQL, используйте `sa` учетной записи, значение `sapassword` из секрета, вы создали и этот IP-адрес.

Пример:

```cmd
sqlcmd -S 104.42.50.138 -U sa -P "MyC0m9l&xP@ssw0rd"
```

![Подключение с помощью sqlcmd](./media/tutorial-sql-server-ag-containers-kubernetes/sqlcmdConnect.png)

Вы также можете подключиться с помощью [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md).

Чтобы проверить подключение, к экземпляру SQL Server, на котором размещена первичная реплика выполните следующий запрос:

```sql
SELECT @@SERVERNAME;
```

Запрос возвращает имя экземпляра SQL Server, на котором размещена первичная реплика.

На этом этапе в кластере Kubernetes есть три экземпляра SQL Server в контейнерах docker. Группа доступности распространяется на все три экземпляра SQL Server, но база данных не входит в группу доступности. Следующим шагом является добавление базы данных к группе доступности.

## <a name="add-a-database-to-the-availability-group"></a>Добавление базы данных в группу доступности

Добавление базы данных к группе доступности:

1. Создание базы данных

  ```sql
  CREATE DATABASE [DemoDB]
  ```

1. Создание полной резервной копии базы данных, чтобы начать цепочку журналов транзакций

  ```sql
  BACKUP DATABASE [DemoDB] 
  TO  DISK = N'/var/opt/mssql/data/DemoDB.bak' 
    WITH NOFORMAT, 
    NOINIT,  
    NAME = N'DemoDB-Full Database Backup', 
    SKIP, 
    NOREWIND, 
    NOUNLOAD,  
    STATS = 10;
  GO
  ```

1. Добавьте базу данных к группе доступности

  ```sql
  ALTER AVAILABILITY GROUP ag1 ADD DATABASE [DemoDB]; 
  ```

Реплика автоматически настраивается режим автоматического заполнения, группы доступности заполняющий базу данных на вторичных репликах.

В SQL Server Management Studios можно подключиться к первичной реплике и на панели мониторинга группы доступности см. в разделе.

Ниже приведен пример группы доступности с репликами на трех узлах, настроенных в панели мониторинга.

![Панель мониторинга AG1](./media/tutorial-sql-server-ag-containers-kubernetes/ssms_AG1.png)

## <a name="verify-failure-and-recovery"></a>Проверка восстановления

Для проверки обнаружения сбоев и отработки отказа можно удалить pod, на котором размещена первичная реплика. Kubernetes будет выбрать новую первичную реплику и перенаправление прослушивателя. Затем он будет повторно создать удаленные pod. 

Чтобы продемонстрировать этот процесс, выполните следующие действия:

1. Список модулей pod SQL Server.

   ```azurecli
   kubectl get pods
   ```

2. Определение модулей pod первичной реплики.

   Либо подключиться к первичной реплике, с помощью внешнего IP-адреса и запроса `@@servername` или использовать `kubectl` для получения соответствующих pod. Эта команда возвращает имя pod, который включает в себя выполнение первичная реплика группы Доступности контейнера:

   ```azurecli
   kubectl get pods --selector="role.ag.mssql.microsoft.com/ag1"="primary" --output=jsonpath={.items..metadata.name}
   ```

3. Удалите модуль.

   ```azurecli
   kubectl delete pod <podName>
   ```

Замените `<podName>` значением, возвращенным из предыдущего шага для имя модуля. 

Kubernetes автоматически выполняет отработку отказа для одной из вторичных реплик, доступных синхронизации, а также повторно создает удаленные pod.

## <a name="clean-up-resources"></a>Очистка ресурсов

Если больше не нужен, удалите группу ресурсов и все связанные ресурсы. Выполните следующую команду:
>[!WARNING]
>Эта команда полностью удаляет все, что в группе ресурсов. Ни один из компонентов в кластере Kubernetes будут доступны, после удаления группы ресурсов.

```azurecli
az group delete --name <MyResourceGroup>
```

Чтобы выполнить приведенную выше команду, замените `<MyResourceGroup>` с именем группы ресурсов. 

Azure удаляет группу ресурсов.

## <a name="summary"></a>Сводка

В этом руководстве вы узнали, как:  

> [!div class="checklist"]
> * Создание хранилища
> * Развертывание оператора SQL Server в кластере Kubernetes 
> * Создание секретов для Kubernetes
> * Развертывание экземпляров SQL Server и работоспособности агентов
> * Подключитесь к первичной реплике
> * Добавление базы данных в группу доступности

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
>[Общие сведения о Kubernetes](http://docs.microsoft.com/azure/aks/intro-kubernetes)
>[управления SQL Server в Kubernetes](sql-server-linux-kubernetes-manage.md)
