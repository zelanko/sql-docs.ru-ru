---
title: Мониторинг и устранение неполадок
titleSuffix: SQL Server big data clusters
description: Эта статья содержит полезные команды для мониторинга и устранения неполадок кластера SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 232c39e6a98f7f55fa3a653735f39c9607fbcbf4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800740"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>Мониторинг и устранение неполадок с кластерами больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается несколько полезных команд Kubernetes, которые можно использовать для наблюдения и диагностики кластера SQL Server 2019 больших данных (Предварительная версия). Показано, как просмотреть подробные сведения о pod или другие артефакты Kubernetes, расположенные в кластере больших данных. В этой статье также рассматриваются общие задачи, такие как копирование файлов в контейнер, под управлением одной из служб SQL Server больших данных кластера.

> [!TIP]
> Выполните следующую команду, **kubectl** команды на клиентском компьютере Linux (bash) или Windows (cmd или PS). Они требуют предыдущей проверки подлинности в кластере и контекста кластера для выполнения. Например, ранее созданного кластера AKS запуском `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` для загрузки файла конфигурации кластера Kubernetes и задать контекст кластера.

## <a name="get-status-of-pods"></a>Получение состояния модулей

Можно использовать `kubectl get pods` команду, чтобы получить состояние модулей POD в кластере для всех пространств имен или пространства имен кластера больших данных. В следующих разделах показаны оба примера.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Показать состояние всех модулей POD в кластере Kubernetes

Выполните следующую команду для получения всех модулей POD, а также их состояние, включая модули, которые являются частью пространства имен модулей кластера больших данных создаются в SQL Server:

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Показать состояние всех модулей POD в кластере SQL Server больших данных

Используйте `-n` параметр для указания определенному пространству имен. Обратите внимание на то, что модули кластера больших данных SQL Server создаются в новое пространство имен, созданные во время начальной загрузки кластера, на основе имени кластера, указанный в файле конфигурации развертывания. Имя по умолчанию `mssql-cluster`, используется здесь.

```bash
kubectl get pods -n mssql-cluster
```

Вы должны увидеть результат, аналогичный приведенному ниже для кластера работает больших данных:

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
> Во время развертывания модулей с **состояние** из **ContainerCreating** по-прежнему в ближайшее время. Если развертывание перестает отвечать на запросы по любой причине, это может послужить идею где проблема может быть. Также рассмотрим **ГОТОВЫ** столбца. Это означает, сколько контейнеров начали в pod. Обратите внимание на то, что развертывание может занять более 30 минут в зависимости от конфигурации и сети. Основная часть этого времени расходуется загрузки образов контейнеров для различных компонентов.

## <a name="get-pod-details"></a>Получение сведений о pod

Выполните следующую команду, чтобы получить подробное описание конкретных pod в выходных данных формата JSON. Он содержит сведения, такие как текущий узел Kubernetes, pod помещенное, контейнеров, выполняемых в pod и изображения, используемого для начальной загрузки контейнеров. Также показывает другие сведения, такие как метки, состояние и сохраняются утверждений тома, которые связаны с pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

В следующем примере показано подробные сведения о `master-0` pod в кластере больших данных с именем `mssql-cluster`:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

При возникновении любых ошибок, вы увидите иногда ошибка в последних событий для модуля.

## <a name="get-pod-logs"></a>Получение журналов pod

Вы можете извлечь журналы для контейнеров, запущенных в модуле. Следующая команда извлекает журналы для всех контейнеров, запущенных в модуль с именем `master-0` и выводит их в файл с именем `master-0-pod-logs.txt`:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a> Получение состояния службы

Выполните следующую команду, чтобы получить сведения для службы кластеров больших данных. Эти сведения включают в себя их типа и связанные IP-адресов с соответствующей службы и порты. Обратите внимание на то, что службы кластера больших данных SQL Server создаются в новое пространство имен, созданные во время начальной загрузки кластера, на основе имени кластера, указанный в файле конфигурации развертывания.

```bash
kubectl get svc -n <namespace_name>
```

В следующем примере показано состояние служб в кластере больших данных с именем `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

Внешние подключения к кластеру больших данных поддерживают такие службы:

| Служба | Описание |
|---|---|
| **master-svc-external** | Предоставляет доступ к основной экземпляр.<br/>(**EXTERNAL-IP, 31433** и **SA** пользователя) |
| **контроллер svc-external** | Поддержка средств и клиентов, управления кластером. |
| **mgmtproxy-svc-external** | Предоставляет доступ к [портал администрирования кластера](cluster-admin-portal.md).<br/>(https://**EXTERNAL-IP**: 30777: портал) |
| **шлюз svc-external** | Предоставляет доступ к шлюзу HDFS или Spark.<br/>(**EXTERNAL-IP** и **корневой** пользователя) |
| **appproxy-svc-external** | Поддерживает сценарии развертывания приложения. |

> [!TIP]
> Это способ просмотра службы, **kubectl**, но можно также использовать `mssqlctl cluster endpoint list` команду, чтобы просмотреть эти конечные точки. Дополнительные сведения см. в разделе [получить конечные точки кластера больших данных](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Получение сведений о службе

Выполните следующую команду, чтобы получить подробное описание службы в выходных данных формата JSON. Оно будет содержать сведения как метки, выбор IP-адрес, внешний IP-адрес (если служба имеет тип подсистемы балансировки нагрузки), порта и т. д.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

Следующий пример извлекает подробные сведения о **master-svc-external** службы:

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>Выполнение команд в контейнере

Если существующие средства или инфраструктуры не включен для выполнения определенной задачи в действительности не в контексте контейнера, вы можете войти в контейнер с помощью `kubectl exec` команды. Например может потребоваться проверить, если существует определенный файл, или может потребоваться перезапуск служб в контейнере. 

Чтобы использовать `kubectl exec` команды, используйте следующий синтаксис:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

В следующих двух разделах два примера выполнения команды в определенном контейнере.

### <a id="restartsql"></a> Войдите в систему, к конкретному контейнеру и перезапустите процесс SQL Server

В следующем примере показано, как повторный запуск процесса SQL Server в `mssql-server` контейнера в `master-0` pod:

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> Войдите в систему, к конкретному контейнеру и перезапустите службы в контейнере
 
В следующем примере показано, как перезапустить все службы, под управлением **supervisord**: 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a> Копирование файлов

Если вам нужно скопировать файлы из контейнера на локальный компьютер, используйте `kubectl cp` команду со следующим синтаксисом:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

Аналогично, можно использовать `kubectl cp` скопировать файлы с локального компьютера в определенном контейнере.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a> Скопируйте файлы из контейнера

Следующий пример копирует файлы журналов SQL Server из контейнера для `~/temp/sqlserverlogs` путь на локальном компьютере (в этом примере локальный компьютер — это клиент для Linux):

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Скопируйте файлы в контейнер

Следующая команда копирует **AdventureWorks2016CTP3.bak** файла с локального компьютера в контейнер главного экземпляра SQL Server (`mssql-server`) в `master-0` pod. Скопировать файл в `/tmp` каталог в контейнере. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a> Принудительного удаления pod
 
Не рекомендуется для принудительного удаления pod. Однако для тестирования доступности, устойчивости и постоянного хранения, пользователь может удалить pod для имитации сбоя pod с `kubectl delete pods` команды.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

В следующем примере удаляется pod пула хранения, `storage-0-0`:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a> Получить IP-адресом модуля
 
Для устранения неполадок, может потребоваться получить IP-адрес узла, в которой группа контейнеров pod в настоящее время выполняется. Чтобы получить IP-адрес, используйте `kubectl get pods` команду со следующим синтаксисом:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

Следующий пример получает IP-адрес узла `master-0` pod работает на:

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="cluster-administration-portal"></a>Портал администрирования кластера

Используйте [портал администрирования кластера](cluster-admin-portal.md) для наблюдения за состоянием кластера больших данных. Например, во время развертывания, можно использовать **развертывания** вкладки. Вам придется ждать для **mgmtproxy-svc-external** службы для запуска до доступа к этому порталу, поэтому он не будет доступен в начале развертывания.

## <a name="kubernetes-dashboard"></a>Панель мониторинга Kubernetes

Можно запустить панель мониторинга Kubernetes, Дополнительные сведения о кластере. В следующих разделах для запуска панели мониторинга для Kubernetes в AKS, а также для загрузки с помощью kubeadm Kubernetes.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Запуск панели мониторинга, если кластер работает в AKS

Для запуска панели мониторинга Kubernetes запустить:

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Если возникнет следующая ошибка: *Не удается прослушать порт 8001: Все прослушиватели не удалось создать из-за следующих ошибок: Не удалось создать прослушиватель: Ошибка прослушивания tcp4 127.0.0.1:8001: > привязки: Обычно разрешается только одно использование адреса сокета (протокол/сетевой адрес и порт). Не удалось создать прослушиватель: Ошибка прослушивания tcp6: адрес [[:: 1]]: 8001: отсутствует порт в > Устранение ошибок: Не удается прослушать любой из запрошенного портов: [{8001 9090}]* , убедитесь, что вы не запускали панели мониторинга уже в другом окне.

При запуске панели мониторинга в браузере, может получить разрешение предупреждения из-за RBAC, включаемой по умолчанию в кластерах AKS и учетной записи службы, используемой панели мониторинга не имеет достаточных разрешений для доступа ко всем ресурсам (например,  *модули POD запрещено: Пользователя «системы: serviceaccount:kube-системы: kubernetes-панель мониторинга» не удалось составить список модулей в пространстве имен «default»* ). Выполните следующую команду, чтобы предоставить необходимые разрешения для `kubernetes-dashboard`, а затем перезапустите панель мониторинга:

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Запуск панели мониторинга, когда начальную загрузку кластера Kubernetes с помощью kubeadm

Для подробные инструкции, как развертывать и настройки панели мониторинга кластера Kubernetes, см. в разделе [в документации по Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Для запуска панели мониторинга Kubernetes, выполните следующую команду:

```bash
kubectl proxy
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server с большими данными](big-data-cluster-overview.md).
