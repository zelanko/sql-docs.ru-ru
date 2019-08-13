---
title: Управление группой доступности Always On SQL Server в Kubernetes
description: Эта статья описывает управление группой доступности Always On SQL Server в Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 893e502c35ae33ce6ff87efd88049db97a40f875
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952541"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Управление группой доступности Always On SQL Server в Kubernetes

Чтобы управлять группой доступности Always On в Kubernetes, создайте манифест и примените его к кластеру. Манифест представляет собой файл `.yaml`.  

Примеры в этой статье применимы ко всему кластеру Kubernetes. Сценарии в этих примерах применяются к кластеру в Службе Azure Kubernetes.

Пример полного развертывания см. в статье [Развертывание группы доступности Always On SQL Server в кластере Kubernetes](sql-server-linux-kubernetes-deploy.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Отработка отказа — группа доступности SQL Server в Kubernetes

Для отработки отказа или перемещения первичной реплики на другой узел в группе доступности сделайте следующее.

1. Определите задание в файле манифеста.

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) в репозитории GitHub [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) описывает задание отработки отказа.

  Скопируйте файл манифеста на терминал администрирования.

  Обновите файл для своей среды.

  - Замените `<containerName>` именем pod (например, mssql2-0) ожидаемого целевого объекта группы доступности.
  - Если группа доступности находится не в пространстве имен `ag1`, замените `ag1` на пространство имен.

  Этот файл определяет задание отработки отказа с именем `manual-failover`.

1. Чтобы развернуть задание, используйте `kubectl apply`. Следующий скрипт развертывает это задание.

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  Когда задание развернуто, Kubernetes с помощью оператора SQL Server выполняет следующие задачи.
  
  - Понижает первичную реплику до вторичной.
  
  - Повышает указанную реплику до первичной.
  
  После применения файла манифеста Kubernetes запускает задание. Задание заставляет супервизора выбрать нового лидера и переместить первичную реплику на экземпляр SQL Server этого лидера.

1. Убедитесь, что задание завершено.
  
  После того как Kubernetes запустит задание, вы можете проверить журнал.
  
  Следующий пример возвращает состояние задания с именем `manual-failover`.

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. Удалите задание отработки отказа вручную. 

  >[!IMPORTANT]
  >Вам нужно вручную удалить задание перед выполнением другой отработки отказа вручную.
  > 
  >Объект задания в Kubernetes сохраняется после завершения, поэтому можно просмотреть его состояние. Вам нужно вручную удалить старые задания после изучения их состояния. При удалении задания также удаляются и журналы Kubernetes. Если не удалять задание, последующие задания отработки отказа завершатся неудачей (если только не изменить имя задания и селектор pod). Дополнительные сведения см. в статье [Задания — выполнение до завершения](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

  Следующая команда удаляет задание.

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>Смена учетных данных

Смените учетные данные, чтобы сбросить пароль для учетной записи `sa` SQL Server и [главный ключ службы](../relational-databases/security/encryption/service-master-key.md) SQL Server. 

Для выполнения этой задачи создайте секреты в кластере Kubernetes, а затем задание для смены учетных данных.

Перед сменой учетных данных создайте секрет для пароля и главного ключа.

Следующий скрипт создает секрет с именем `new-sql-secrets`. Перед запуском скрипта замените `<>` сложными паролями для `sapassword` и `masterkeypassword`. Используйте разные пароли для каждого соответствующего значения.

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

Выполните указанные ниже действия для каждого экземпляра SQL Server, которому требуется главный ключ или пароль `sa`.

1. Скопируйте [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) на терминал администрирования.

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) в репозитории GitHub [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) — это пример манифеста для этого задания.

  Перед применением этого манифеста обновите манифест для среды. При необходимости проверьте и измените указанные ниже параметры.

  - Проверьте пространство имен. При необходимости внесите изменения. Следующий пример в манифесте применяется к пространству имен с именем `ag1`.

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - Проверьте имя экземпляра SQL Server. При необходимости внесите изменения. Следующий пример в спецификации манифеста применяется к экземпляру SQL Server с именем `mssql1`.

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  Сохраните обновленный файл манифеста на рабочей станции.

1. Используйте `kubectl` для развертывания задания.

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes обновляет главный ключ и пароль `sa` для одного экземпляра SQL Server в группе доступности.

1. Убедитесь, что задание завершено. Выполните следующую команду: Чтобы убедиться, что задание завершено, выполните следующую команду. 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  После выполнения задания обновляются главный ключ и пароль `sa` для одного экземпляра SQL Server.


1. Перед повторным запуском задания удалите его. Имя каждого задания должно быть уникальным.

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

Чтобы задать одинаковый пароль `sa` для всех экземпляров SQL Server, повторите описанные выше действия для каждого экземпляра SQL Server.

## <a name="next-steps"></a>Следующие шаги

[Доступ к панели мониторинга Kubernetes с помощью Службы Kubernetes Azure (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Группа доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
