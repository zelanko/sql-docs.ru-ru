---
title: Высокий уровень доступности для контейнеров SQL Server
description: В этой статье рассматриваются высокого уровня доступности для контейнеров SQL Server
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: ccf4b3bab89c29fde1ff592a166baa3747afa890
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843229"
---
# <a name="high-availability-for-sql-server-containers"></a>Высокий уровень доступности для контейнеров SQL Server

Создание и управление экземплярами SQL Server непосредственно на платформе Kubernetes.

Развертывание SQL Server в контейнеры docker под управлением [Kubernetes](https://kubernetes.io/). В Kubernetes контейнер с экземпляром SQL Server могут автоматически восстанавливать в случае сбоя узла кластера. Для более высокий уровень доступности Настройка SQL Server Always On группы доступности с экземплярами SQL Server в контейнеры в кластере Kubernetes. В этой статье сравниваются эти два решения.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Сравнение версий SQL Server в Kubernetes

SQL Server 2017 предоставляет образ Docker, можно развернуть в Kubernetes. Изображение можно настроить с помощью Kubernetes утверждение постоянного тома (PVC). Kubernetes отслеживает процесс SQL Server в контейнере. При сбое процесса, pod, контейнера или узел Kubernetes автоматически обеспечивает начальную загрузку другого экземпляра и выполняет повторное подключение к хранилищу.

SQL Server 2019 представляет более надежной archicture с Kubernetes StatefulSet. Это позволяет Kubernetes для управления экземплярами SQL Server в образах контейнеров, которые могут участвовать в SQL Server всегда группу доступности. Это обеспечивают улучшенные наблюдения за состоянием системы, более быстрое восстановление, разгрузка резервного копирования и чтения scale out.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Контейнер с экземпляром SQL Server в Kubernetes

Kubernetes 1.6 и более поздних версий имеется поддержка [ *классы хранения*](http://kubernetes.io/docs/concepts/storage/storage-classes/), [ *утверждения постоянного тома*](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)и [  *Тип тома дисков Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

В этой конфигурации Kubernetes играет роль оркестратора контейнеров. 

![Схема кластера Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — это экземпляр SQL Server (контейнер) в [ *pod*](http://kubernetes.io/docs/concepts/workloads/pods/pod/). Объект [реплика](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует, что модуль автоматическое восстановление после сбоя узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, на котором размещена IP-адресом, которое изменяется после выхода из строя `mssql-server`.

Kubernetes управляет ресурсами кластера. После сбоя узла на котором размещается экземпляр SQL Server в контейнере или pod, orchestrator обеспечивает начальную загрузку контейнера в идентичный модуль с экземпляром SQL Server и присоединяет его к то же постоянное хранилище.

SQL Server 2017 и более поздних версий поддержка контейнеров в Kubernetes.

Для создания контейнера в Kubernetes, см. в разделе [развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Группу доступности SQL Server Always On, в контейнерах SQL Server в Kubernetes

SQL Server 2019 поддерживает группы доступности на контейнеры в Kubernetes. Для групп доступности, развертывание SQL Server [Kubernetes оператор](http://coreos.com/blog/introducing-operators.html) к кластеру Kubernetes. Оператор помогает упаковывать, развертывания и управления экземплярами SQL Server и группы доступности в кластере.

![Группы Доступности в контейнере Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

В приведенном выше рисунке кластер kubernetes с четырьмя узлами размещается группа доступности с тремя репликами. Решение включает в себя следующие компоненты:

* Kubernetes [ *развертывания*](http://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Развертывание включает оператор и карту конфигурации. Они предоставляют образ контейнера, программного обеспечения и инструкции, необходимые для развертывания экземпляров SQL Server для группы доступности.

* Три узла, каждый из которых размещает [ *StatefulSet*](http://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). StatefulSet содержит pod. Содержит каждым pod:
  * Контейнер SQL Server одного экземпляра SQL Server.
  * Начальнику `mcr.microsoft.com/mssql/ha` управление группой доступности.

* Два [ *ConfigMaps* ](http://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) связаны с группой доступности. ConfigMaps содержат следующие сведения:
  * Развертывание для оператора.
  * Группа доступности.

 * Постоянные тома для каждого экземпляра SQL Server предоставляют хранилище для файлов данных и журналов.

Кроме того, кластер сохраняет [ *секреты* ](http://kubernetes.io/docs/concepts/configuration/secret/) пароли, сертификаты, ключи и другие конфиденциальные сведения.

## <a name="compare-sql-server-high-availabiltiy-on-containers-with-and-without-the-availability-group"></a>Сравнение SQL Server высокой доступности на контейнеры без группы доступности

Следующие таблицы compairs возможность высокой доступности SQL Server в контейнерах на Kubernetes с и без группы доступности:

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

Одно из основных отличий является быстрее с группой доступности, чем с одним экземпляром SQL Server в контейнере времени восстановления (или отработки отказа). Это, так как группы доступности SQL Server сохраняет вторичные реплики баз данных группы доступности на других узлах в кластере. При отработке отказа вторичной реплики выбран и повышению до основного. Приложениям, подключенным к службе перенаправляются на новой первичной репликой. 

Без группы доступности Kubernetes обнаруживает отработку отказа, необходимо создать контейнер, подключите его к хранилищу и подключили приложений, подключенных к службе. Время точное отработки отказа зависит от того, где было отработки отказа, и как он был обнаружен. 

Как правило время отработки отказа для группы доступности измеряется в секундах, пока время отработки отказа для одного экземпляра для восстановления контейнер может быть до 10 минут.

## <a name="next-steps"></a>Следующие шаги

Чтобы развернуть контейнеры SQL Server в службе Azure Kubernetes (AKS), выполните одно из этих учебников.

* [Развертывание SQL Server в контейнере Docker](sql-server-linux-configure-docker.md)
* [Развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Развертывание SQL Server группы доступности Always On Kubernetes](tutorial-sql-server-ag-kubernetes.md)

