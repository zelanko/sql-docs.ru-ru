---
title: Группы доступности Always On для контейнеров под управлением Linux
titleSuffix: SQL Server
description: В этой статье рассматриваются группы доступности в контейнерах SQL Server
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cb9775ad0fce022fb2bd5f8fda02f7e198d1c6fa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713587"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>Группы доступности AlwaysOn для SQL Server контейнеров

SQL Server 2019 поддерживает группы доступности на контейнеры в кластере Kubernetes. Для групп доступности, развертывание SQL Server [Kubernetes оператор](https://coreos.com/blog/introducing-operators.html) к кластеру Kubernetes. Оператор помогает упаковывать, развертывать и администрировать группы доступности в кластере.

![Группы Доступности в контейнере Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

В приведенном выше рисунке кластеров kubernetes с четырьмя узлами размещения группы доступности с тремя репликами. Решение включает в себя следующие компоненты:

* Kubernetes [ *развертывания*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Развертывание включает оператор и карту конфигурации. Они предоставляют образ контейнера, программного обеспечения и инструкции, необходимые для развертывания экземпляров SQL Server для группы доступности.

* Три узла, каждый из которых размещает [ *StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). Содержит StatefulSet [ *pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Содержит каждым pod:
  * Контейнер SQL Server одного экземпляра SQL Server.
  * Агент группы доступности. 

* Два [ *ConfigMaps* ](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) связаны с группой доступности. ConfigMaps содержат следующие сведения:
  * Развертывание для оператора.
  * Группа доступности.

 * [*Постоянные тома* ](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) — части хранилища. Объект *утверждение постоянного тома* (PVC) — это запрос для хранилища пользователя. Каждый контейнер связан с утверждение постоянного тома для хранения данных и журналов. В службе Kubernetes Azure (AKS), вы [создать утверждение постоянного тома](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) для автоматически подготовки хранилища на основе класса хранения.


Кроме того, кластер сохраняет [ *секреты* ](https://kubernetes.io/docs/concepts/configuration/secret/) пароли, сертификаты, ключи и другие конфиденциальные сведения.

## <a name="deploy-the-availability-group-in-kubernetes"></a>Развертывание группы доступности в Kubernetes

Развертывание группы доступности в Kubernetes:

1. Создание кластера Kubernetes

   Для группы доступности необходимо создайте по крайней мере три узла для SQL Server, а также узел для шаблона.

1. Развертывание оператора

1. Настройка хранилища

1. Развертывание StatefulSet

   Оператор ожидает передачи данных для инструкции по развертыванию StatefulSet. Автоматически создает экземпляры SQL Server на трех отдельных узлах и настроит группу доступности с диспетчером внешних кластера.

1. Создание баз данных и присоединить их к группе доступности

Подробные инструкции см. в разделе [группы доступности AlwaysOn для SQL Server контейнеров](sql-server-ag-kubernetes.md).

## <a name="sql-server-kubernetes-operator"></a>Оператор SQL Server Kubernetes

После развертывания оператора, он регистрирует пользовательских ресурсов SQL Server. Оператор для развертывания этого ресурса.  Каждый ресурс, соответствующий экземпляр SQL Server и включает в себя определенные свойства, такие как `sapassword` и `monitoring policy`. Оператор выполняет синтаксический анализ ресурсов и развертывает Kubernetes StatefulSet.

StatfulSet содержит:

* mssql-server container

* контейнер MSSQL-ha-"контролер"

Код для оператора, контролер высокого уровня ДОСТУПНОСТИ и SQL Server упаковывается в образ Docker с именем `mcr.microsoft.com/mssql/ha`. Этот образ содержит следующие двоичные файлы:

* `mssql-operator`

    Этот процесс развертывается как отдельное развертывание Kubernetes. Он регистрирует [настраиваемых ресурсов Kubernetes](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) вызывается `SqlServer` (sqlservers.mssql.microsoft.com). Затем он ожидает передачи данных для таких ресурсов создается или обновляется в кластере Kubernetes. Для каждого такого события, он создает или обновляет ресурсы Kubernetes для соответствующего экземпляра (например StatefulSet или `mssql-server-k8s-init-sql` задания).

* `mssql-server-k8s-health-agent`

    Этот веб-сервер обслуживает Kubernetes [проверки активности](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) для определения работоспособности экземпляра SQL Server. Отслеживание работоспособности локального экземпляра SQL Server путем вызова `sp_server_diagnostics` и сравнить результаты с политикой монитора.

* `mssql-ha-supervisor`

   Поддерживает ag сертификата и конечной точки. 

* `mssql-server-k8s-ag-agent`
  
    Этот процесс отслеживает работоспособность реплики группы Доступности на одном экземпляре SQL Server и выполняет переход на другой ресурс.

    Кроме того, обеспечена лидера.

* `mssql-server-k8s-init-sql`
  
    Этот Kubernetes [задания](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) применяет настройки требуемого состояния для экземпляра SQL Server. Задание создается с помощью оператора, каждый раз при создании или обновлении ресурса SqlServer. Он гарантирует, что целевой экземпляр SQL Server, соответствующий настраиваемого ресурса имеет требуемой конфигурацией, описанной в ресурсе.

    Например если параметры являются обязательными, оно будет завершено их:
  * Обновить пароль системного Администратора
  * Создает имя входа SQL для агентов
  * Создает конечную точку зеркального Отображения

* `mssql-server-k8s-rotate-creds`
  
    Это задание Kubernetes реализует задачу поворот учетные данные. Создание этого задания, чтобы запросить обновления пароль системного Администратора, пароль для входа агента SQL, DBM cert и т. д. Пароль системного Администратора указываются в виде параметров задания. Остальные создаются автоматически.

* `mssql-server-k8s-failover`

   Задание Kubernetes, реализующий рабочий процесс на другой ресурс вручную.

### <a name="notes"></a>Примечания

Независимо от конфигурации группы Доступности оператор будет всегда следует развертывать контролер высокого уровня ДОСТУПНОСТИ. Если ресурс SqlServer, не содержит ни одной такой Группе, оператор будет по-прежнему развертывать этот контейнер.

Версия образа оператор идентична версии для образа SQL Server.

## <a name="next-steps"></a>Следующие шаги

> [SQL Server контейнера в Kubernetes](tutorial-sql-server-containers-kubernetes.md)
