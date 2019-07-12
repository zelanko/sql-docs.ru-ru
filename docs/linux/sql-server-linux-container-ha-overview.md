---
title: Высокий уровень доступности для контейнеров SQL Server
description: В этой статье рассматриваются высокого уровня доступности для контейнеров SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: da4c702e8ec5e8c1d645af616df53edd287eae5a
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833917"
---
# <a name="high-availability-for-sql-server-containers"></a>Высокий уровень доступности для контейнеров SQL Server

Создание и управление экземплярами SQL Server непосредственно на платформе Kubernetes.

Развертывание SQL Server в контейнеры docker под управлением [Kubernetes](https://kubernetes.io/). В Kubernetes контейнер с экземпляром SQL Server могут автоматически восстанавливать в случае сбоя узла кластера. Для более высокий уровень доступности Настройка SQL Server Always On группы доступности с экземплярами SQL Server в контейнеры в кластере Kubernetes. В этой статье сравниваются эти два решения.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Сравнение версий SQL Server в Kubernetes

SQL Server 2017 предоставляет образ Docker, можно развернуть в Kubernetes. Изображение можно настроить с помощью Kubernetes утверждение постоянного тома (PVC). Kubernetes отслеживает процесс SQL Server в контейнере. При сбое процесса, pod, контейнера или узел Kubernetes автоматически обеспечивает начальную загрузку другого экземпляра и выполняет повторное подключение к хранилищу.

2019 SQL Server (Предварительная версия) предоставляет более надежной архитектуры с Kubernetes StatefulSet. Kubernetes управляет экземплярами SQL Server в образах контейнеров, которые участвуют в SQL Server всегда группу доступности. Этот шаблон предоставляет улучшенное наблюдение, более быстрое восстановление, резервное копирование разгрузки и чтения горизонтальное масштабирование.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Контейнер с экземпляром SQL Server в Kubernetes

Kubernetes 1.6 и более поздних версий имеется поддержка [ *классы хранения*](https://kubernetes.io/docs/concepts/storage/storage-classes/), [ *утверждения постоянного тома*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)и [  *Тип тома дисков Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

В этой конфигурации Kubernetes играет роль оркестратора контейнеров. 

![Схема кластера Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — это экземпляр SQL Server (контейнер) в [ *pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Объект [реплика](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует, что модуль автоматическое восстановление после сбоя узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, на котором размещена IP-адресом, которое изменяется после выхода из строя `mssql-server`.

Kubernetes управляет ресурсами кластера. При сбое узла, на котором размещается контейнер экземпляра SQL Server, он загружает новый контейнер с экземпляром SQL Server и присоединяет его к то же постоянное хранилище.

SQL Server 2017 и более поздних версий поддержка контейнеров в Kubernetes.

Для создания контейнера в Kubernetes, см. в разделе [развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Группу доступности SQL Server Always On, в контейнерах SQL Server в Kubernetes

SQL Server 2019 поддерживает группы доступности на контейнеры в Kubernetes. Для групп доступности, развертывание SQL Server [Kubernetes оператор](https://coreos.com/blog/introducing-operators.html) к кластеру Kubernetes. Оператор помогает упаковывать, развертывания и управления экземплярами SQL Server и группы доступности в кластере.

![Группы Доступности в контейнере Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

В приведенном выше рисунке кластер kubernetes с четырьмя узлами размещается группа доступности с тремя репликами. Решение включает в себя следующие компоненты:

* Kubernetes [ *развертывания*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Развертывание включает оператор и карту конфигурации. Развертывание описывает образ контейнера, программного обеспечения и инструкции, необходимые для развертывания экземпляров SQL Server для группы доступности.

* Три узла, каждый из которых размещает [ *StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). StatefulSet содержит pod. Содержит каждым pod:
  * Контейнер SQL Server одного экземпляра SQL Server.
  * Начальнику `mcr.microsoft.com/mssql/ha` управление группой доступности.

* Два [ *ConfigMaps* ](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) связаны с группой доступности. ConfigMaps содержат следующие сведения:
  * Развертывание для оператора.
  * Группа доступности.

 * Постоянные тома для каждого экземпляра SQL Server предоставляют хранилище для файлов данных и журналов.

Кроме того, кластер сохраняет [ *секреты* ](https://kubernetes.io/docs/concepts/configuration/secret/) пароли, сертификаты, ключи и другие конфиденциальные сведения.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Сравнение высокого уровня доступности SQL Server в контейнеры без группы доступности

В следующей таблице сравниваются возможности высокого уровня доступности SQL Server в контейнерах на Kubernetes и без группы доступности:

| |С группой доступности | Автономный экземпляр контейнера<br/> Без групп доступности
|:------|:------|:------
|Автоматическое восстановление после сбоя узла | Да | Да
|Автоматическое восстановление после сбоя pod | Да | Да
|Быстрее выполнить отработку отказа |Да |
|Автоматическое восстановление после сбоя экземпляра SQL Server | Да | 
|Автоматическое восстановление после сбоя при проверке работоспособности базы данных | Да | 
|Укажите реплик только для чтения | Да |
|Резервное копирование вторичной реплики | Да | 
|Работает в виде StatefulSet | Да | 

Одно из основных отличий является быстрее с группой доступности, чем с одним экземпляром SQL Server в контейнере времени восстановления (или отработки отказа). Это улучшение — так как группы доступности SQL Server хранит вторичной реплики на другие узлы в кластере. При отработке отказа вторичной реплики выбран и повышению до основного. Приложениям, подключенным к службе перенаправляются на новой первичной репликой.

Без группы доступности Kubernetes обнаруживает отработку отказа, необходимо создать контейнер, подключите его к хранилищу и подключили приложений, подключенных к службе. Время точное отработки отказа зависит от того, где было отработки отказа, и как он был обнаружен. 

Как правило время отработки отказа для группы доступности измеряется в секундах, пока время отработки отказа для одного экземпляра для восстановления контейнер может быть до 10 минут.

## <a name="next-steps"></a>Следующие шаги

Чтобы развернуть контейнеры SQL Server в службе Azure Kubernetes (AKS), см. следующие примеры:

* [Развертывание SQL Server в контейнере Docker](sql-server-linux-configure-docker.md)
* [Развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Группы доступности AlwaysOn для SQL Server контейнеров](sql-server-ag-kubernetes.md)

