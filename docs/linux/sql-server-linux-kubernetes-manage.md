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
ms.openlocfilehash: 8ad318c0f0967f26f5cfdf2c5ad9af2d94323bf0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622842"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Управление SQL Server Always On Availability Group Kubernetes

Для управления всегда группы доступности на платформе Kubernetes, создайте манифест и применить ее к кластеру. Манифест `.yaml` файл.  

В примерах в этой статье применяются ко всем кластере Kubernetes. В этих примерах, применяются к кластер в службе Azure Kubernetes.

Пример развертывания end-to-end в [учебником](tutorial-sql-server-ag-kubernetes.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Отработка отказа — группы доступности SQL Server в Kubernetes

Чтобы выполнить отработку отказа первичной реплики группы доступности на другой узел в Kubernetes, используйте задание. В этой статье определяет переменные среды для этого задания.

В следующем примере создается файл манифеста содержит описание задания вручную выполнить отработку отказа задания для группы доступности в реплике Kubernetes. Скопируйте содержимое этого примера в новый файл с именем `failover.yaml`.

[FailOver.yaml](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates/failover.yaml)

Чтобы развернуть задание, используйте `Kubectl`.

```azurecli
kubectl apply -f failover.yaml
```

При применении файл манифеста Kubernetes запускает задание. При запуске задания, контролер выбирает новый лидера и перемещение первичной реплики к экземпляру SQL Server, лидера.

После запуска задания, удалите его. Объект задания в Kubernetes остается после завершения, чтобы просмотреть его состояние. Необходимо вручную удалить старые задания после отметить их состояние. При удалении задания также удаляются журналы Kubernetes. Если вы не удалите задание, будущих отработки отказа будут завершаться, если не изменить имя задания и селектор pod. Дополнительные сведения см. в разделе [до завершения выполнения заданий -](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

## <a name="rotate-credentials"></a>Смена учетных данных

Смена учетных данных для обновления сопоставления безопасности и главный ключ.

Копировать [повернуть creds.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) локально воспользоваться `kubectl` для применения его к кластеру.

```azurecli
kubectl apply -f rotate-creds.yaml
```

## <a name="next-steps"></a>Следующие шаги

[Доступ к панели мониторинга Kubernetes со службой Azure Kubernetes (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
