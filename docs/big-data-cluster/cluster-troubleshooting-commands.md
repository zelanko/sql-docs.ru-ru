---
title: Мониторинг и устранение неполадок
titleSuffix: SQL Server big data clusters
description: Эта статья содержит полезные команды для мониторинга и устранения неполадок в кластере больших данных SQL Server 2019 (Предварительная версия).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 272249b7bd6c22895b7d10e7fbce4a20cb647a49
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419479"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>Мониторинг и устранение неполадок SQL Server кластерах больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются несколько полезных команд Kubernetes, которые можно использовать для отслеживания и устранения неполадок в кластере SQL Server 2019 больших данных (Предварительная версия). Здесь показано, как просмотреть подробные сведения о Pod или других артефактах Kubernetes, расположенных в кластере больших данных. В этой статье также рассматриваются распространенные задачи, такие как копирование файлов в контейнер или из него, где выполняется одна из SQL Server служб кластеров больших данных.

> [!TIP]
> Выполните следующие команды **kubectl** на клиентском компьютере Windows (cmd или PS) или Linux (bash). Они нуждаются в предыдущей проверке подлинности в кластере и контексте кластера для выполнения. Например, для ранее созданного кластера AKS можно запустить `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` , чтобы скачать файл конфигурации кластера Kubernetes и задать контекст кластера.

## <a name="get-status-of-pods"></a>Получение состояния модулей Pod

С помощью `kubectl get pods` команды можно получить состояние модулей Pod в кластере для всех пространств имен или пространств имен кластера больших данных. В следующих разделах показаны примеры обоих типов.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Отображение состояния всех модулей Pod в кластере Kubernetes

Выполните следующую команду, чтобы получить все модули Pod и их состояния, включая модули, которые являются частью пространства имен, в котором создаются модули кластера больших данных SQL Server созданы в.

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Отображение состояния всех модулей Pod в кластере SQL Server больших данных

Используйте параметр `-n` , чтобы указать определенное пространство имен. Обратите внимание, что SQL Server модули больших данных кластера создаются в новом пространстве имен, созданном во время начальной загрузки кластера, на основе имени кластера, указанного в файле конфигурации развертывания. Используется имя `mssql-cluster`по умолчанию,.

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
> Во время развертывания модули Pod с  состоянием **контаинеркреатинг** по-прежнему появятся. Если развертывание по какой либо причине зависает, это может дать вам идею, где может быть проблема. Также взгляните на столбец **Ready (Готово** ). Это говорит о том, сколько контейнеров началось в Pod. Обратите внимание, что развертывание может занять 30 минут или более в зависимости от конфигурации и сети. Значительная часть этого времени потратила на загрузку образов контейнеров для различных компонентов.

## <a name="get-pod-details"></a>Получение сведений о Pod

Выполните следующую команду, чтобы получить подробное описание конкретного Pod в выходных данных формата JSON. Сюда входят такие сведения, как текущий узел Kubernetes, на котором размещен модуль Pod, контейнеры, работающие в Pod, и образ, используемый для начальной загрузки контейнеров. Здесь также отображаются другие сведения, такие как метки, состояние и утвержденные тома, связанные с модулем Pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

В следующем примере показаны сведения для `master-0` Pod в кластере больших данных с именем: `mssql-cluster`

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

В случае возникновения ошибок может возникнуть ошибка в последних событиях для Pod.

## <a name="get-pod-logs"></a>Получение журналов Pod

Вы можете получить журналы для контейнеров, работающих в Pod. Следующая команда извлекает журналы для всех контейнеров, работающих в Pod `master-0` , и выводит их в имя `master-0-pod-logs.txt`файла:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a>Получение состояния служб

Выполните следующую команду, чтобы получить сведения о службах кластеров больших данных. Эти сведения включают в себя их тип и IP-адреса, связанные с соответствующими службами и портами. Обратите внимание, что SQL Server службы кластеров больших данных создаются в новом пространстве имен, созданном во время начальной загрузки кластера, на основе имени кластера, указанного в файле конфигурации развертывания.

```bash
kubectl get svc -n <namespace_name>
```

В следующем примере показано состояние для служб в кластере больших данных с именем `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

Следующие службы поддерживают внешние подключения к кластеру больших данных:

| Служба | Описание |
|---|---|
| **Главный-SVC-External** | Предоставляет доступ к главному экземпляру.<br/>(**External-IP, 31433** и пользователь **SA** ) |
| **контроллер-SVC-External** | Поддерживает средства и клиенты, управляющие кластером. |
| **Шлюз-SVC-External** | Предоставляет доступ к шлюзу HDFS/Spark.<br/>(**External-IP** и **привилегированный** пользователь) |
| **апппрокси-SVC-External** | Поддержка сценариев развертывания приложений. |

> [!TIP]
> Это способ просмотра служб с помощью **kubectl**, но можно также использовать `azdata bdc endpoint list` команду для просмотра этих конечных точек. Дополнительные сведения см. в разделе [получение конечных точек кластера больших данных](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Получение сведений о службе

Выполните эту команду, чтобы получить подробное описание службы в выходных данных формата JSON. Он будет включать такие сведения, как метки, селекторы, IP-адреса, внешние IP (если служба имеет тип подсистемы балансировки нагрузки), порт и т. д.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

В следующем примере извлекаются сведения о **внешней службе Master-SVC** :

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>Выполнение команд в контейнере

Если существующие средства или инфраструктура не позволяют выполнять определенную задачу без фактического включения в контекст контейнера, можно войти в контейнер с помощью `kubectl exec` команды. Например, может потребоваться проверить, существует ли конкретный файл, или же потребуется перезапустить службы в контейнере. 

Чтобы использовать `kubectl exec` команду, используйте следующий синтаксис:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Следующие два раздела содержат два примера выполнения команды в определенном контейнере.

### <a id="restartsql"></a>Войдите в конкретный контейнер и перезапустите процесс SQL Server

В следующем примере показано, как перезапустить процесс SQL Server в `mssql-server` контейнере `master-0` в модуле Pod:

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a>Войдите в конкретный контейнер и перезапустите службы в контейнере.
 
В следующем примере показано, как перезапустить все **службы, управляемые**администратором: 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a>Копирование файлов

Если необходимо скопировать файлы из контейнера на локальный компьютер, используйте `kubectl cp` команду со следующим синтаксисом:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

Аналогичным образом можно использовать `kubectl cp` для копирования файлов с локального компьютера в конкретный контейнер.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a>Копирование файлов из контейнера

В следующем примере файлы журнала SQL Server копируются из контейнера в `~/temp/sqlserverlogs` путь на локальном компьютере (в этом примере локальный компьютер является клиентом Linux):

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a>Копирование файлов в контейнер

В следующем примере файл **базе adventureworks2016ctp3. bak** копируется с локального компьютера в контейнер экземпляра SQL Server master (`mssql-server`) в `master-0` модуле Pod. Файл копируется `/tmp` в каталог в контейнере. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a>Принудительное удаление Pod
 
Не рекомендуется принудительно удалять Pod. Но для тестирования доступности, устойчивости или сохраняемости данных можно удалить модуль Pod, чтобы имитировать сбой Pod с помощью `kubectl delete pods` команды.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

В следующем примере удаляется модуль `storage-0-0`пула носителей:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a>Получение IP-адреса Pod
 
В целях устранения неполадок может потребоваться получить IP-адрес узла, на котором сейчас выполняется модуль. Чтобы получить IP-адрес, используйте `kubectl get pods` команду со следующим синтаксисом:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

В следующем примере показано получение IP-адреса узла, `master-0` на котором работает модуль Pod:

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="kubernetes-dashboard"></a>Панель мониторинга Kubernetes

Для получения дополнительных сведений о кластере можно запустить панель мониторинга Kubernetes. В следующих разделах объясняется, как запустить панель мониторинга для Kubernetes на AKS и для Kubernetes с начальной загрузкой с помощью кубеадм.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Запуск панели мониторинга при работе кластера в AKS

Чтобы запустить панель мониторинга Kubernetes, выполните следующие действия.

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> При возникновении следующей ошибки: *Не удалось прослушать порт 8001: Не удалось создать все прослушиватели со следующими ошибками: Не удалось создать прослушиватель: Ошибка прослушивания tcp4 127.0.0.1:8001: > BIND: Обычно разрешено использование только одного адреса сокета (протокол/сетевой адрес/порт). Не удалось создать прослушиватель: Ошибка прослушивания tcp6: адрес [[:: 1]]: 8001: отсутствует порт в > Ошибка адреса: Не удалось прослушать ни один из запрошенных портов: [{8001 9090}* ] Убедитесь, что панель мониторинга не была запущена из другого окна.

При запуске панели мониторинга в браузере могут появиться предупреждения о разрешениях, так как RBAC включен по умолчанию в кластерах AKS, а учетная запись службы, используемая панелью мониторинга, не имеет достаточных разрешений для доступа ко  *всем ресурсам (например, модули Pod запрещены: Пользователь "System: учетная запись службы: KUBE-System: kubernetes-Dashboard" не может составить список модулей Pod в пространстве*имен "default". Выполните следующую команду, чтобы предоставить необходимые разрешения для `kubernetes-dashboard`, а затем перезапустите панель мониторинга:

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Запуск панели мониторинга при начальной загрузке кластера Kubernetes с помощью кубеадм

Подробные инструкции по развертыванию и настройке панели мониторинга в кластере Kubernetes см. [в документации по Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Чтобы запустить панель мониторинга Kubernetes, выполните следующую команду:

```bash
kubectl proxy
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [что такое SQL Server кластерами больших данных](big-data-cluster-overview.md).
