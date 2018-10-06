---
title: Управление SQL Server группы доступности Always On Kubernetes
description: В этой статье описывается управление SQL Server всегда группу доступности в Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7f713ed7dd5d0260df6441698371b33f94813d7e
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251981"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Управление SQL Server Always On Availability Group Kubernetes

Для управления всегда группы доступности на платформе Kubernetes, создайте манифест и применить ее к кластеру. Манифест `.yaml` файл.  

В примерах в этой статье применяются ко всем кластере Kubernetes. В этих примерах, применяются к кластер в службе Azure Kubernetes.

Ознакомиться с примером полное развертывание в [группы доступности AlwaysOn для SQL Server контейнеров](sql-server-ag-kubernetes.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Отработка отказа — группы доступности SQL Server в Kubernetes

Чтобы выполнить отработку отказа первичной реплики группы доступности на другой узел в Kubernetes, используйте задание. В этой статье определяет переменные среды для этого задания.

Следующий файл манифеста содержит описание задания вручную выполнить отработку отказа группы доступности. 

Скопируйте содержимое этого примера в новый файл с именем `failover.yaml`.

[FailOver.yaml](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates/failover.yaml)

Чтобы развернуть задание, используйте `Kubectl`.

```azurecli
kubectl apply -f failover.yaml
```

После установки файл манифеста Kubernetes запускает задание. Задание делает контролер выбрать нового лидера и перемещение первичной реплики к экземпляру SQL Server, лидера.

После запуска задания, удалите его. Объект задания в Kubernetes остается после завершения, чтобы просмотреть его состояние. Необходимо вручную удалить старые задания после отметить их состояние. При удалении задания также удаляются журналы Kubernetes. Если не удалить задание, задания будущих отработки отказа завершится ошибкой, если не изменить имя задания и селектор pod. Дополнительные сведения см. в разделе [до завершения выполнения заданий -](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

## <a name="rotate-credentials"></a>Смена учетных данных

Смена учетных данных для обновления сопоставления безопасности и главный ключ.

Копировать [повернуть creds.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) локально воспользоваться `kubectl` для применения его к кластеру.

```azurecli
kubectl apply -f rotate-creds.yaml
```

## <a name="next-steps"></a>Следующие шаги

[Доступ к панели мониторинга Kubernetes со службой Azure Kubernetes (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
