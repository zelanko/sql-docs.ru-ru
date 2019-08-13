---
title: Подключение к группе доступности Always On SQL Server в кластере Kubernetes
description: Эта статья описывает, как подключиться к группе доступности Always On.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f05bc51f587723414d3b0a4090fe2b27ad5fb837
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952607"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Подключение к группе доступности Always On SQL Server в Kubernetes

Чтобы подключиться к экземплярам SQL Server в контейнерах в кластере Kubernetes, создайте [службу балансировки нагрузки ](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). Подсистема балансировки нагрузки является конечной точкой. Она содержит IP-адрес и перенаправляет запросы на него в pod, где выполняется экземпляр SQL Server.

Чтобы подключиться к реплике группы доступности, создайте службу для разных типов реплик. Примеры служб для различных типов реплик см. в [sql-server-samples/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

* `ag1-primary` указывает на первичную реплику.
* `ag1-secondary` указывает на вторичную реплику.

При наличии нескольких вторичных реплик Kubernetes направляет ваше подключение на разные реплики по принципу циклического перебора.

## <a name="create-a-load-balancer-service"></a>Создание службы балансировки нагрузки

Чтобы создать службы балансировки нагрузки для первичного экземпляра и реплик, скопируйте [`ag1-services.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) из [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file) и измените его для группы доступности.

Следующая команда применяет конфигурацию из файла `.yaml` к кластеру.

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Получение IP-адреса для службы балансировки нагрузки

Чтобы получить IP-адрес для своей службы балансировки нагрузки, выполните следующую команду.

```kubectl
kubectl get services
```

Определите IP-адрес службы, к которой требуется подключиться.

## <a name="connect-to-primary-replica"></a>Подключение к первичной реплике

Чтобы подключиться к первичной реплике с использованием проверки подлинности SQL, используйте учетную запись `sa`, значение для `sapassword` из созданного секрета и этот IP-адрес.

Пример:

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Следующие шаги

[Управление группой доступности SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-manage.md)

[Группа доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
