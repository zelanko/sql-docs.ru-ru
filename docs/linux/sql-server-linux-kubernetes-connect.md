---
title: Подключиться к SQL Server группы доступности AlwaysOn в кластере Kubernetes
description: В этой статье объясняется, как подключиться к группе доступности AlwaysOn
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d13f89a1297d21c882075821a681886dc95c4c76
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049594"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Подключение к SQL Server Always On Availability Group в Kubernetes

Чтобы подключиться к экземплярам SQL Server в контейнеры в кластере Kubernetes, создайте [служба балансировки нагрузки](http://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). Подсистема балансировки нагрузки переадресовывает запросы для IP-адреса к pod, на котором запущен экземпляр SQL Server.

Чтобы подключиться к реплике группы доступности, создайте службу для типов другую реплику. Вы можете ознакомиться с примерами служб для различных типов реплик в [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml).

* `ag1-primary` Указывает на первичной реплике.
* `ag1-secondary-sync` Указывает синхронная вторичная реплика.
* `ag1-secondary-async` Указывает асинхронной вторичной реплики.

Если существует более одного вторичной реплики того же типа, Kubernetes направляет подключение к разные реплики в циклического перебора.

## <a name="create-a-load-balancer-service"></a>Создание службы балансировки нагрузки

Чтобы создать службу балансировки нагрузки для первичной реплики, скопируйте `ag1-primary.yaml` из [sql-server-samples]()и обновить его для своей группы доступности.

Следующая команда применяет yaml-файл в кластере:

```kubectl
kubectl apply -f ag1-primary.yaml
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Получить IP-адрес для службы балансировки нагрузки

Чтобы получить IP-адрес балансировщика нагрузки для службы балансировки нагрузки, выполните

```kubectl
kubectl get services
```

Определите IP-адрес службы, которую вы хотите подключиться.

## <a name="connect-to-primary-replica"></a>Подключитесь к первичной реплике

Чтобы подключиться к первичной реплике с проверкой подлинности SQL, используйте `sa` учетной записи, значение `sapassword` из секрета, вы создали и этот IP-адрес.

Пример:

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Следующие шаги

[Управление группой доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-manage.md)

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)