---
title: Группы доступности Always On для контейнеров с Linux
titleSuffix: SQL Server
description: В этой статье описываются группы доступности в контейнерах SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3910c74be803b7fc63c8bf560fc637387e06ee15
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67910468"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>Группы доступности Always On для контейнеров SQL Server

SQL Server 2019 поддерживает группы доступности в контейнерах в кластере Kubernetes. Для групп доступности разверните [оператор Kubernetes](https://coreos.com/blog/introducing-operators.html) SQL Server для кластера Kubernetes. Этот оператор используется для упаковки, развертывания группы доступности в кластере и управления ею.

![Группа доступности в контейнере Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

На приведенном выше рисунке в кластере Kubernetes из четырех узлов размещается группа доступности с тремя репликами. Это решение включает следующие компоненты:

* [*Развертывание*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) Kubernetes. Развертывание включает оператор и карту конфигурации. Таким образом, предоставляются образ контейнера, программное обеспечение и инструкции, необходимые для развертывания экземпляров SQL Server для группы доступности.

* Три узла, в каждом из которых размещается [*набор с отслеживанием состояния*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). Набор с отслеживанием состояния содержит [*pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Каждый pod содержит:
  * Контейнер SQL Server, в котором выполняется один экземпляр SQL Server.
  * Агент группы доступности. 

* Две [*карты конфигурации*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/), связанные с группой доступности. Карта конфигурации предоставляет информацию о следующих компонентах:
  * Развертывание для оператора.
  * Группа доступности.

 * [*Постоянные тома*](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) являются частями хранилища. *Утверждение постоянного тома* (PVC) — это запрос к хранилищу со стороны пользователя. Каждый контейнер связан с утверждением постоянного тома для хранения данных и журналов. В службе Azure Kubernetes (AKS) [утверждение постоянного тома создается](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) для автоматической подготовки хранилища на основе класса хранилища.


Кроме того, в кластере хранятся [*секреты*](https://kubernetes.io/docs/concepts/configuration/secret/) для паролей, сертификатов, ключей и другой конфиденциальной информации.

## <a name="deploy-the-availability-group-in-kubernetes"></a>Развертывание группы доступности в Kubernetes

Развертывание группы доступности в Kubernetes:

1. Создание кластера Kubernetes

   Для группы доступности необходимо создать как минимум три узла для SQL Server и один узел для главного экземпляра.

1. Развертывание оператора

1. Настройка хранилища

1. Развертывание набора с отслеживанием состояния

   Оператор принимает инструкции по развертыванию набора с отслеживанием состояния. Он автоматически создает экземпляры SQL Server на трех отдельных узлах и настраивает группу доступности с помощью внешнего диспетчера кластеров.

1. Создание баз данных и их присоединение к группе доступности

Подробные инструкции см. в статье [Группы доступности Always On для контейнеров SQL Server](sql-server-ag-kubernetes.md).

## <a name="sql-server-kubernetes-operator"></a>Оператор Kubernetes SQL Server

После развертывания оператор регистрирует пользовательский ресурс SQL Server. Используйте этот оператор для развертывания ресурса.  Каждый ресурс соответствует экземпляру SQL Server и включает определенные свойства, такие как `sapassword` и `monitoring policy`. Оператор анализирует ресурс и развертывает набор Kubernetes с отслеживанием состояния.

Набор с отслеживанием состояния содержит:

* Контейнер mssql-server

* Контейнер mssql-ha-supervisor

Код для оператора, супервизора высокого уровня доступности и SQL Server упакован в образ Docker с именем `mcr.microsoft.com/mssql/ha`. Этот образ содержит следующие двоичные файлы:

* `mssql-operator`

    Этот процесс развертывается в рамках отдельного развертывания Kubernetes. Он регистрирует [пользовательский ресурс Kubernetes](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) с именем `SqlServer` (sqlservers.mssql.microsoft.com). После этого он прослушивает события создания или обновления таких ресурсов в кластере Kubernetes. Для каждого такого события создаются или обновляются ресурсы Kubernetes для соответствующих экземпляров (например, набор с отслеживанием состояния или задание `mssql-server-k8s-init-sql`).

* `mssql-server-k8s-health-agent`

    Этот веб-сервер выполняет [пробы активности](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) Kubernetes для определения работоспособности экземпляра SQL Server. Работоспособность локального экземпляра SQL Server отслеживается путем вызова `sp_server_diagnostics` и сравнения результатов с политикой мониторинга.

* `mssql-ha-supervisor`

   Также поддерживаются сертификат группы доступности и конечная точка. 

* `mssql-server-k8s-ag-agent`
  
    Этот процесс отслеживает работоспособность реплики группы доступности на отдельном экземпляре SQL Server и выполняет отработку отказа.

    Кроме того, но осуществляет выбор лидера.

* `mssql-server-k8s-init-sql`
  
    Это [задание](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) Kubernetes применяет конфигурацию требуемого состояния к экземпляру SQL Server. Это задание создается оператором каждый раз при создании или обновлении ресурса SqlServer. Таким образом, гарантируется, что целевой экземпляр SQL Server, соответствующий пользовательскому ресурсу, будет иметь нужную конфигурацию, описываемую в ресурсе.

    Например, при необходимости выполняются следующие настройки:
  * Обновление пароля системного администратора
  * Создание имен входа SQL для агентов
  * Создание конечной точки зеркального отображения базы данных

* `mssql-server-k8s-rotate-creds`
  
    Это задание Kubernetes реализует задачу циклической смены учетных данных. Создайте это задание, чтобы запрашивать обновления пароля системного администратора, пароля для входа агента SQL, сертификата зеркального отображения базы данных и т. д. Пароль системного администратора задается в параметрах задания. Остальные элементы создаются автоматически.

* `mssql-server-k8s-failover`

   Задание Kubernetes, реализующее рабочий процесс ручной отработки отказа.

### <a name="notes"></a>Примечания

Независимо от конфигурации группы доступности оператор всегда будет развертывать супервизор высокого уровня доступности. Если ресурс SqlServer не содержит ни одной группы доступности, оператор по-прежнему будет развертывать этот контейнер.

Версия для образа оператора идентична версии для образа SQL Server.

## <a name="next-steps"></a>Следующие шаги

> [Контейнер SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)
