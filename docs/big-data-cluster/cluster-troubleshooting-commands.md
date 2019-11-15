---
title: Мониторинг и устранение неполадок
titleSuffix: SQL Server big data clusters
description: Эта статья содержит полезные команды для мониторинга и устранения неполадок в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e70689d1e4891fefde8fd1feb76b081bc14bfe81
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153634"
---
# <a name="monitoring-and-troubleshoot-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Мониторинг и устранение неполадок [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается несколько полезных команд Kubernetes, которые можно использовать для отслеживания и устранения неполадок в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Здесь показано, как просмотреть подробные сведения о Pod или других артефактах Kubernetes, расположенных в кластере больших данных. В этой статье также рассматриваются распространенные задачи, такие как копирование файлов в контейнере, где выполняется одна из служб кластеров больших данных SQL Server.

> [!TIP]
> Для мониторинга состояния компонентов кластеров больших данных можно использовать команды [**azdata bdc status**](deployment-guidance.md#status) или встроенные [записные книжки для устранения неполадок](manage-notebooks.md) в составе Azure Data Studio.

> [!TIP]
> Выполните следующие команды **kubectl** на клиентском компьютере Windows (cmd или PS) или Linux (bash). Они нуждаются в предварительной проверке подлинности в кластере и контексте кластера для выполнения. Например, для ранее созданного кластера AKS можно запустить `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>`, чтобы скачать файл конфигурации кластера Kubernetes и задать контекст кластера.

## <a name="get-status-of-pods"></a>Получение состояния модулей Pod

С помощью команды `kubectl get pods` можно получить состояние модулей Pod в кластере для всех пространств имен или пространства имен кластера больших данных. В следующих разделах показаны примеры обоих типов.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Отображение состояния всех модулей Pod в кластере Kubernetes

Выполните следующую команду, чтобы получить все модули Pod и их состояния, включая модули, которые являются частью пространства имен, в котором созданы модули кластера больших данных SQL Server.

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Отображение состояния всех модулей Pod в кластере больших данных SQL Server

Используйте параметр `-n`, чтобы указать определенное пространство имен. Обратите внимание, что модули кластера больших данных SQL Server создаются в новом пространстве имен, созданном во время начальной загрузки кластера на основе имени кластера, указанного в файле конфигурации развертывания. Здесь используется имя по умолчанию — `mssql-cluster`.

```bash
kubectl get pods -n mssql-cluster
```

Для работающего кластера больших данных вы должны увидеть результат, аналогичный приведенному ниже.

```output
PS C:\> kubectl get pods -n mssql-cluster
NAME              READY   STATUS    RESTARTS   AGE
appproxy-f2qqt    2/2     Running   0          110m
compute-0-0       3/3     Running   0          110m
control-zlncl     4/4     Running   0          118m
data-0-0          3/3     Running   0          110m
data-0-1          3/3     Running   0          110m
gateway-0         2/2     Running   0          109m
logsdb-0          1/1     Running   0          112m
logsui-jtdnv      1/1     Running   0          112m
master-0          7/7     Running   0          110m
metricsdb-0       1/1     Running   0          112m
metricsdc-shv2f   1/1     Running   0          112m
metricsui-9bcj7   1/1     Running   0          112m
mgmtproxy-x6gcs   2/2     Running   0          112m
nmnode-0-0        1/1     Running   0          110m
storage-0-0       7/7     Running   0          110m
storage-0-1       7/7     Running   0          110m
```

> [!NOTE]
> Во время развертывания модули Pod со значением **STATUS** (Состояние), равным **ContainerCreating** (Создается контейнер), по-прежнему отображаются. Если развертывание по какой либо причине зависает, это может подсказать вам, где может быть проблема. Также взгляните на столбец **READY** (Готово). Это говорит о том, сколько контейнеров запущено в Pod. Обратите внимание, что развертывание может занять 30 минут или более в зависимости от конфигурации и сети. Значительная часть этого времени тратится на скачивание образов контейнеров для различных компонентов.

## <a name="get-pod-details"></a>Получение сведений о Pod

Выполните следующую команду, чтобы получить подробное описание конкретного Pod в выходных данных формата JSON. Сюда входят такие сведения, как текущий узел Kubernetes, на котором размещен модуль Pod, контейнеры, работающие в Pod, и образ, используемый для начальной загрузки контейнеров. Здесь также отображаются другие сведения, такие как метки, состояние и постоянные тома, связанные с модулем Pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

В следующем примере показаны сведения для Pod `master-0` в кластере больших данных с именем `mssql-cluster`:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

В случае возникновения ошибок может присутствовать ошибка в последних событиях Pod.

## <a name="get-pod-logs"></a>Получение журналов Pod

Вы можете получить журналы контейнеров, работающих в Pod. Следующая команда извлекает журналы для всех контейнеров, работающих в Pod `master-0`, и выводит их в файл `master-0-pod-logs.txt`:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluster > master-0-pod-logs.txt
```

## <a id="services"></a> Получение состояния служб

Выполните следующую команду, чтобы получить сведения о службах кластеров больших данных. Эти сведения включают в себя их тип и IP-адреса, связанные с соответствующими службами и портами. Обратите внимание, что службы кластера больших данных SQL Server создаются в новом пространстве имен, созданном во время начальной загрузки кластера на основе имени кластера, указанного в файле конфигурации развертывания.

```bash
kubectl get svc -n <namespace_name>
```

В следующем примере показаны сведения о состоянии служб в кластере больших данных с именем `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

Следующие службы поддерживают внешние подключения к кластеру больших данных:

| Служба | Описание |
|---|---|
| **master-svc-external** | Предоставляет доступ к главному экземпляру.<br/>(**EXTERNAL-IP,31433** и пользователь **SA**) |
| **controller-svc-external** | Поддерживает средства и клиенты, управляющие кластером. |
| **gateway-svc-external** | Предоставляет доступ к шлюзу HDFS/Spark.<br/>(**EXTERNAL-IP** и пользователь **root**) |
| **appproxy-svc-external** | Поддержка сценариев развертывания приложений. |

> [!TIP]
> Это способ просмотра служб с помощью **kubectl**, но для просмотра этих конечных точек можно также использовать команду `azdata bdc endpoint list`. Дополнительные сведения см. в разделе [Получение конечных точек кластера больших данных](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Получение сведений о службе

Выполните следующую команду, чтобы получить подробное описание конкретной службы в выходных данных формата JSON. Оно будет включать такие сведения, как метки, селектор, IP-адреса, внешние IP-адреса (если служба имеет тип подсистемы балансировки нагрузки), порт и т. д.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

В следующем примере извлекаются сведения о службе **master-svc-external**:

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a id="copy"></a> Копирование файлов

Если необходимо скопировать файлы из контейнера на локальный компьютер, используйте команду `kubectl cp` со следующим синтаксисом:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

Аналогичным образом можно использовать `kubectl cp` для копирования файлов с локального компьютера в конкретный контейнер.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a> Копирование файлов из контейнера

В следующем примере файлы журнала SQL Server копируются из контейнера в путь `~/temp/sqlserverlogs` на локальном компьютере (в этом примере локальный компьютер является клиентом Linux):

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Копирование файлов в контейнер

В следующем примере файл **AdventureWorks2016CTP3.bak** копируется с локального компьютера в контейнер главного экземпляра SQL Server (`mssql-server`) в модуле Pod `master-0`. Файл копируется в каталог `/tmp` в контейнере. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a> Принудительное удаление Pod
 
Принудительно удалять Pod не рекомендуется. Однако для тестирования доступности, устойчивости или сохраняемости данных можно удалить модуль Pod, чтобы имитировать сбой Pod, с помощью команды `kubectl delete pods`.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

В следующем примере удаляется модуль Pod пула носителей, `storage-0-0`:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a> Получение IP-адреса Pod
 
В целях устранения неполадок может потребоваться получить IP-адрес узла, на котором сейчас выполняется модуль. Чтобы получить IP-адрес, используйте команду `kubectl get pods` со следующим синтаксисом:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

В следующем примере показано получение IP-адреса узла, на котором работает модуль Pod `master-0`:

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="kubernetes-dashboard"></a>Панель мониторинга Kubernetes

Для получения дополнительных сведений о кластере можно запустить панель мониторинга Kubernetes. В следующих разделах объясняется, как запустить панель мониторинга для Kubernetes на AKS и для Kubernetes, подготовленного с помощью kubeadm.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Запуск панели мониторинга при работе кластера в AKS

Чтобы запустить панель мониторинга Kubernetes, выполните следующие действия.

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Если возникает следующее сообщение об ошибке: *Не удалось прослушать порт 8001: не удалось создать прослушиватели со следующими ошибками: Не удалось создать прослушиватель: ошибка прослушивания tcp4 127.0.0.1:8001: >bind: обычно разрешено только одно использование каждого адреса сокета (протокол/сетевой адрес/порт). Не удалось создать прослушиватель: ошибка прослушивания tcp6: адрес [[::1]]: 8001: отсутствует порт в > ошибка адреса: не удалось прослушать ни один из запрошенных портов: [{8001 9090}]* , убедитесь, что панель мониторинга не была запущена из другого окна.

При запуске панели мониторинга в браузере могут появиться предупреждения о разрешениях, так как RBAC включен по умолчанию в кластерах AKS, а учетная запись службы, используемая панелью мониторинга, не имеет достаточных разрешений для доступа ко всем ресурсам (например, *модули Pod запрещены: пользователь "system:serviceaccount:kube-system:kubernetes-dashboard" не может получить список модулей Pod в пространстве имен "default"* ). Выполните следующую команду, чтобы предоставить необходимые разрешения для `kubernetes-dashboard`, а затем перезапустите панель мониторинга:

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Запуск панели мониторинга при начальной загрузке кластера Kubernetes с помощью kubeadm

Подробные инструкции по развертыванию и настройке панели мониторинга в кластере Kubernetes см. в [документации по Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Чтобы запустить панель мониторинга Kubernetes, выполните команду:

```bash
kubectl proxy
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).
