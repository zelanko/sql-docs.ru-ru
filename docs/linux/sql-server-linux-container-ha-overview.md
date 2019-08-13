---
title: Высокий уровень доступности для контейнеров SQL Server
description: В этой статье описывается обеспечение высокого уровня доступности в контейнерах SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: aa54849c16ea9dfb821404b553b1e9183b61d66a
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68077474"
---
# <a name="high-availability-for-sql-server-containers"></a>Высокий уровень доступности для контейнеров SQL Server

Создание собственных экземпляров SQL Server в собственном коде Kubernetes и управление ими.

Развертывание SQL Server в контейнерах Docker под управлением [Kubernetes](https://kubernetes.io/). В Kubernetes контейнер с экземпляром SQL Server может автоматически восстанавливаться в случае отказа узла кластера. Чтобы обеспечить более высокий уровень доступности, настройте группу доступности SQL Server Always On с экземплярами SQL Server в контейнерах в кластере Kubernetes. В рамках данной статьи проводится сравнение этих двух решений.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Сравнение версий SQL Server в Kubernetes

В состав SQL Server 2017 входит образ Docker, который можно развертывать в Kubernetes. Вы можете использовать для настройки этого образа утверждение постоянного тома Kubernetes (PVC). Kubernetes отслеживает процесс SQL Server в контейнере. В случае сбоя процесса, pod, контейнера или узла Kubernetes автоматически загружает другой экземпляр и восстанавливает подключение к хранилищу.

В предварительной версии SQL Server 2019 представлена более надежная архитектура на основе набора Kubernetes с отслеживанием состояния. Kubernetes управляет экземплярами SQL Server в образах контейнера, которые участвуют в группе доступности SQL Server Always On. Такой подход позволяет повысить эффективность мониторинга работоспособности, ускорить процесс восстановления, а также оптимизировать нагрузку резервного копирования и масштабирование операций чтения.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Контейнер с экземпляром SQL Server в Kubernetes

В Kubernetes версии 1.6 и более поздних поддерживаются [*классы хранилища*](https://kubernetes.io/docs/concepts/storage/storage-classes/), [*утверждения постоянного тома*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims), а также [*тип тома диска Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

В этой конфигурации Kubernetes играет роль оркестратора контейнера. 

![Схема кластера Kubernetes с SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — это экземпляр SQL Server (контейнер) в [*pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Применение [набора реплик](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует автоматическое восстановление pod в случае отказа узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, которая содержит IP-адрес, остающийся неизменным в случае отказа `mssql-server`.

Kubernetes управляет ресурсами в кластере. В случае отказа узла, на котором размещается контейнер экземпляра SQL Server, осуществляется загрузка нового контейнера экземпляра SQL Server, который привязывается к тому же постоянному хранилищу.

SQL Server 2017 и более поздних версий поддерживает контейнеры в Kubernetes.

Сведения о создании контейнера в Kubernetes см. в статье [Развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Группа доступности SQL Server Always On в контейнерах SQL Server в Kubernetes

SQL Server 2019 поддерживает группы доступности в контейнерах в Kubernetes. Для групп доступности разверните [оператор Kubernetes](https://coreos.com/blog/introducing-operators.html) SQL Server для кластера Kubernetes. Этот оператор используется для упаковки, развертывания экземпляров SQL Server и группы доступности в кластере, а также управления ими.

![Группа доступности в контейнере Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

На приведенном выше рисунке в кластере Kubernetes из четырех узлов размещается группа доступности с тремя репликами. Это решение включает следующие компоненты:

* [*Развертывание*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) Kubernetes. Развертывание включает оператор и карту конфигурации. Такое развертывание описывает образ контейнера, программное обеспечение и инструкции, необходимые для развертывания экземпляров SQL Server для группы доступности.

* Три узла, в каждом из которых размещается [*набор с отслеживанием состояния*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). Набор с отслеживанием состояния содержит pod. Каждый pod содержит:
  * Контейнер SQL Server, в котором выполняется один экземпляр SQL Server.
  * Супервизор `mcr.microsoft.com/mssql/ha`, обеспечивающий управление группой доступности.

* Две [*карты конфигурации*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/), связанные с группой доступности. Карта конфигурации предоставляет информацию о следующих компонентах:
  * Развертывание для оператора.
  * Группа доступности.

 * Постоянные тома для каждого экземпляра SQL Server обеспечивают хранение файлов данных и журналов.

Кроме того, в кластере хранятся [*секреты*](https://kubernetes.io/docs/concepts/configuration/secret/) для паролей, сертификатов, ключей и другой конфиденциальной информации.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Сравнение уровня доступности SQL Server в контейнерах с группой доступности и без нее

В следующей таблице приводится сравнение уровня доступности SQL Server в контейнерах в Kubernetes с группой доступности и без нее:

| |С группой доступности | Изолированный экземпляр контейнера<br/> Без группы доступности
|:------|:------|:------
|Автоматическое восстановление после отказа узла | Да | Да
|Автоматическое восстановление после отказа pod | Да | Да
|Более быстрая отработка отказа |Да |
|Автоматическое восстановление после отказа экземпляра SQL Server | Да | 
|Автоматическое восстановление после сбоя при проверке работоспособности базы данных | Да | 
|Предоставление реплик только для чтения | Да |
|Резервное копирование вторичной реплики | Да | 
|Выполнение в качестве набора с отслеживанием состояния | Да | 

Одно из основных различий заключается в том, что при использовании группы доступности восстановление (отработка отказа) выполняется быстрее по сравнению с одним экземпляром SQL Server в контейнере. Это улучшение связано с тем, что группа доступности SQL Server хранит вторичные реплики других узлов в кластере. При отработке отказа выбирается вторичная реплика, которая повышается до первичной. Приложения, которые подключаются к службе, перенаправляются в новую первичную реплику.

Если группа доступности не используется, при обнаружении отказа Kubernetes требуется создать контейнер, подключить его к хранилищу, а затем повторно подключить приложения, которые были подключены к службе. Точное время отработки отказа зависит от того, где произошел отказ и каким образом он был обнаружен. 

Как правило, время отработки отказа для группы доступности измеряется несколькими секундами, тогда как восстановление контейнера для отдельного экземпляра может занимать до 10 минут.

## <a name="next-steps"></a>Следующие шаги

Информацию о развертывании контейнеров SQL Server в службе Azure Kubernetes (AKS) см. в описании следующих примеров:

* [Развертывание SQL Server в контейнере Docker](sql-server-linux-configure-docker.md)
* [Развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Группы доступности Always On для контейнеров SQL Server](sql-server-ag-kubernetes.md)

