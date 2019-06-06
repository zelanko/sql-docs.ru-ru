---
title: Управление SQL Server группы доступности Always On Kubernetes
description: В этой статье описывается управление SQL Server всегда группу доступности в Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 808f49ff5060ba6a6ffe9e864cfc2710fe6251e6
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705523"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Управление SQL Server Always On Availability Group Kubernetes

Для управления всегда группы доступности на платформе Kubernetes, создайте манифест и применить ее к кластеру. Манифест `.yaml` файл.  

В примерах в этой статье применяются ко всем кластере Kubernetes. В этих примерах, применяются к кластер в службе Azure Kubernetes.

Ознакомиться с примером полное развертывание в [развертывание SQL Server всегда группу доступности в кластере Kubernetes](sql-server-linux-kubernetes-deploy.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Отработка отказа — группы доступности SQL Server в Kubernetes

Чтобы выполнить отработку отказа или перемещение первичной реплики на другой узел в группе доступности, выполните следующие действия:

1. Определение задания в файл манифеста.

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) -в [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) репозиторий github содержит описание задания отработки отказа.

  Скопируйте файл манифеста для администрирования терминала.

  Обновите файл для вашей среды.

  - Замените `<containerName>` pod именем (например mssql2-0) целевую группу предположительно станет доступным.
  - Если группа доступности не находится в `ag1` пространства имен, замените `ag1` с пространством имен.

  Этот файл определяет задание отработки отказа с именем `manual-failover`.

1. Чтобы развернуть задание, используйте `kubectl apply`. Следующий скрипт развертывает задание.

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  После задания развертывания kubernetes с помощью оператора SQL Server, выполняет следующие задачи:
  
  - Можно понизить уровень первичная реплика, базу данных-получатель
  
  - Повышает уровень указанной реплики до первичной
  
  После установки файл манифеста Kubernetes запускает задание. Задание делает контролер выбрать нового лидера и перемещение первичной реплики к экземпляру SQL Server, лидера.

1. Убедитесь, что задание завершено.
  
  После выполнения задания в Kubernetes при просмотре журнала.
  
  В следующем примере возвращается состояние задания с именем `manual-failover`.

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. Удаление задания на другой ресурс вручную. 

  >[!IMPORTANT]
  >Необходимо вручную удалить задание, прежде чем выполнять другой ресурс вручную.
  > 
  >Объект задания в Kubernetes остается после завершения, чтобы просмотреть его состояние. Необходимо вручную удалить старые задания после отметить их состояние. При удалении задания также удаляются журналы Kubernetes. Если не удалить задание, задания будущих отработки отказа завершится ошибкой, если не изменить имя задания и селектор pod. Дополнительные сведения см. в разделе [до завершения выполнения заданий -](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

  Следующая команда удаляет задание.

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>Смена учетных данных

Смена учетных данных для сброса пароля для SQL Server `sa` учетной записи и SQL Server [главного ключа службы](../relational-databases/security/encryption/service-master-key.md). 

Для выполнения этой задачи, будет создание новых секретов в кластере Kubernetes и затем создать задание для поворота учетные данные.

Смена учетных данных, прежде новый секрет пароль и главный ключ.

Следующий скрипт создает секретный код, с именем `new-sql-secrets`. Перед выполнением скрипта замените `<>` сложных паролей `sapassword` и `masterkeypassword`. Используйте разные пароли для каждого соответствующего значения.

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

Выполните следующие действия для каждого экземпляра SQL Server, требуется главный ключ или `sa` пароль.

1. Копировать [ `rotate-creds.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) для администрирования терминала.

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) в [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) репозитории github является примером манифест для этого задания.

  Прежде чем применить этот манифест, обновите манифест для вашей среды. Просмотрите и измените следующие параметры, при необходимости.

  - Проверьте пространство имен. При необходимости обновите. В следующем примере в манифесте, применяется к пространству имен с именем `ag1`.

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - Проверьте имя экземпляра SQL Server. При необходимости обновите. В следующем примере в спецификацию манифеста, применяется к экземпляру SQL Server с именем `mssql1`.

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  Сохраните обновленный файл манифеста на рабочую станцию.

1. Используйте `kubectl` к развертыванию задания.

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes обновляет главного ключа и `sa` пароль для одного экземпляра SQL Server в группе доступности.

1. Убедитесь, что задание завершено. Выполните следующую команду: Чтобы проверить, что задание завершено, запустите 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  После успешного завершения задания, главный ключ и `sa` пароль для одного экземпляра SQL Server будут обновлены.


1. Перед запуском задания, удалите задание. Каждое имя задания должно быть уникальным.

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

Чтобы задать же `sa` пароль для всех экземпляров SQL Server, повторите предыдущие шаги для каждого экземпляра SQL Server.

## <a name="next-steps"></a>Следующие шаги

[Доступ к панели мониторинга Kubernetes со службой Azure Kubernetes (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
