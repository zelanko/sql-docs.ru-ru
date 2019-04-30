---
title: Подключиться к SQL Server группы доступности AlwaysOn в кластере Kubernetes
description: В этой статье объясняется, как подключиться к группе доступности AlwaysOn
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6352fc7be129f485175b1144d14aa380b2d99e1f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63231174"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Подключение к SQL Server Always On Availability Group в Kubernetes

Чтобы подключиться к экземплярам SQL Server в контейнеры в кластере Kubernetes, создайте [служба балансировки нагрузки](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). Подсистема балансировки нагрузки — это конечная точка. Он содержит IP-адресом и перенаправляет запросы для IP-адреса к pod, на котором запущен экземпляр SQL Server.

Чтобы подключиться к реплике группы доступности, создайте службу для типов другую реплику. Вы можете ознакомиться с примерами служб для различных типов реплик в [sql-server примеры/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

* `ag1-primary` Указывает на первичной реплике.
* `ag1-secondary` Указывает на любой из вторичных реплик.

Если более чем одного вторичной реплики, Kubernetes направляет подключение к разные реплики в циклического перебора.

## <a name="create-a-load-balancer-service"></a>Создание службы балансировки нагрузки

Чтобы создать службы подсистемы балансировки нагрузки для основного корпуса и реплик, скопируйте [ `ag1-services.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file) и обновить его для своей группы доступности.

Следующая команда применяет конфигурацию из `.yaml` файла к кластеру:

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
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
