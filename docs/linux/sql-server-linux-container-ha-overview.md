---
title: Высокий уровень доступности для контейнеров SQL Server
description: Сведения о высоком уровне доступности для контейнеров SQL Server. Также вы узнаете о развертывании контейнера с помощью SQL Server в Kubernetes.
author: VanMSFT
ms.author: vanto
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: d7e15c070b17fd0a3682f5572c9b7cd3ce2c1dee
ms.sourcegitcommit: 22102f25db5ccca39aebf96bc861c92f2367c77a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2020
ms.locfileid: "92115657"
---
# <a name="high-availability-for-sql-server-containers"></a>Высокий уровень доступности для контейнеров SQL Server

Создание собственных экземпляров SQL Server в собственном коде Kubernetes и управление ими.

Развертывание SQL Server в контейнерах Docker под управлением [Kubernetes](https://kubernetes.io/). В Kubernetes контейнер с экземпляром SQL Server может автоматически восстанавливаться в случае отказа узла кластера.

В SQL Server 2017 представлен образ Docker, который можно развертывать в Kubernetes. Вы можете использовать для настройки этого образа утверждение постоянного тома Kubernetes (PVC). Kubernetes отслеживает процесс SQL Server в контейнере. В случае сбоя процесса, pod, контейнера или узла Kubernetes автоматически загружает другой экземпляр и восстанавливает подключение к хранилищу.

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Контейнер с экземпляром SQL Server в Kubernetes

В Kubernetes версии 1.6 и более поздних поддерживаются [*классы хранилища*](https://kubernetes.io/docs/concepts/storage/storage-classes/), [*утверждения постоянного тома*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims), а также [*тип тома диска Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

В этой конфигурации Kubernetes играет роль оркестратора контейнера. 

![Схема кластера Kubernetes с SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

На предыдущей схеме `mssql-server` — это экземпляр SQL Server (контейнер) в [*pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Применение [набора реплик](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) гарантирует автоматическое восстановление pod в случае отказа узла. Приложения подключаются к службе. В этом случае служба представляет подсистему балансировки нагрузки, которая содержит IP-адрес, остающийся неизменным в случае отказа `mssql-server`.

Kubernetes управляет ресурсами в кластере. В случае отказа узла, на котором размещается контейнер экземпляра SQL Server, осуществляется загрузка нового контейнера экземпляра SQL Server, который привязывается к тому же постоянному хранилищу.

SQL Server 2017 и более поздних версий поддерживает контейнеры в Kubernetes.

Сведения о создании контейнера в Kubernetes см. в статье [Развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="next-steps"></a>Дальнейшие действия

Информацию о развертывании контейнеров SQL Server в службе Azure Kubernetes (AKS) см. в описании следующих примеров:
* [Развертывание SQL Server в контейнере Docker](./sql-server-linux-docker-container-deployment.md)
* [Развертывание контейнера SQL Server в Kubernetes](tutorial-sql-server-containers-kubernetes.md)