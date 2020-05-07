---
title: Службы машинного обучения (Python, R)
titleSuffix: SQL Server Big Data Clusters
description: Узнайте, как выполнять скрипты Python и R в главном экземпляре кластеров больших данных SQL Server с помощью служб машинного обучения.
author: dphansen
ms.author: davidph
ms.date: 04/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
ms.openlocfilehash: d105db3da8a6732c2884af7e42a71441eef6f077
ms.sourcegitcommit: ed5f063d02a019becf866c4cb4900e5f39b8db18
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82643341"
---
# <a name="run-python-and-r-scripts-with-machine-learning-services-on-sql-server-big-data-clusters"></a>Выполнение скриптов Python и R с помощью служб машинного обучения в кластерах больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Скрипты Python и R можно выполнять в главном экземпляре [кластеров больших данных SQL Server](big-data-cluster-overview.md) с помощью [служб машинного обучения](../machine-learning/index.yml).

> [!NOTE]
> Можно также выполнять код Java в главном экземпляре с помощью [расширений языка для SQL Server](../language-extensions/language-extensions-overview.md). После выполнения описанных ниже действий будут также включены расширения языка.

## <a name="enable-machine-learning-services"></a>Включение служб машинного обучения

Службы машинного обучения устанавливаются в Кластерах больших данных по умолчанию и не требуют отдельной установки.

Чтобы включить службы машинного обучения, выполните следующую инструкцию в главном экземпляре.

```sql
EXEC sp_configure 'external scripts enabled', 1
RECONFIGURE WITH OVERRIDE
GO
```

Теперь все готово для выполнения скриптов Python и R в главном экземпляре кластеров больших данных. Перед тем как запустить первый скрипт, ознакомьтесь с краткими руководствами в разделе [Следующие шаги](#next-steps).

>[!NOTE]
>Параметр конфигурации не может быть задан для соединения прослушивателя группы доступности. Если кластеры больших данных развертываются с высоким уровнем доступности, установите `external scripts enabled` на каждой реплике. См. раздел [Включение кластера с высоким уровнем доступности](#enable-on-cluster-with-high-availability).

## <a name="enable-on-cluster-with-high-availability"></a>Включение кластера с высоким уровнем доступности

При [развертывании кластера больших данных SQL Server с высоким уровнем доступности](deployment-high-availability.md) развертывание создает группу доступности для главного экземпляра. Чтобы включить службы машинного обучения, установите `external scripts enabled` на каждом экземпляре группы доступности. Для кластера больших данных необходимо выполнить `sp_configure` на каждой реплике главного экземпляра SQL Server.

В следующем разделе описано, как включить внешние скрипты для каждого экземпляра.

### <a name="create-an-external-load-balancer-for-each-instance"></a>Создание внешнего балансировщика нагрузки для каждого экземпляра

Для каждой реплики в группе доступности создайте подсистему балансировки нагрузки, которая позволит подключиться к экземпляру. 

`kubectl expose pod <pod-name> --port=<connection port number> --name=<load-balancer-name> --type=LoadBalancer -n <kubernetes namespace>`

В примерах этой статьи мы используем следующие значения:

- `<pod-name>`: `master-#`
- `<connection port number>`: `1533`
- `<load-balancer-name>`: `mymaster-#`
- `<kubernetes namespace>`: `mssql-cluster`

Обновите следующий сценарий для своей среды и выполните команды:

```bash
kubectl expose pod master-0 --port=1533 --name=mymaster-0 --type=LoadBalancer -n mssql-cluster 
kubectl expose pod master-1 --port=1533 --name=mymaster-1 --type=LoadBalancer -n mssql-cluster
kubectl expose pod master-2 --port=1533 --name=mymaster-2 --type=LoadBalancer -n mssql-cluster 
```

`kubectl` возвращает следующие выходные данные.

```bash
service/mymaster-0 exposed
service/mymaster-1 exposed
service/mymaster-2 exposed
```

Каждая подсистема балансировки нагрузки является конечной точкой главной реплики.

### <a name="enable-script-execution-on-each-replica"></a>Включение выполнения скрипта на каждой реплике

1. Получите IP-адрес конечной точки главной реплики.

   Следующая команда возвращает внешний IP-адрес конечной точки реплики. 

   `kubectl get services <load-balancer-name> -n <kubernetes namespace>`

   Чтобы получить внешний IP-адрес для каждой реплики в этом сценарии, выполните следующие команды:

   ```bash
   kubectl get services mymaster-0 -n mssql-cluster
   kubectl get services mymaster-1 -n mssql-cluster
   kubectl get services mymaster-2 -n mssql-cluster
   ```

   >[!NOTE]
   > Внешний IP-адрес будет доступен через некоторое время. Периодически запускайте предыдущий скрипт, пока каждая конечная точка не вернет внешний IP-адрес.

1. Подключитесь к конечной точке главной реплики и разрешите выполнение скрипта.

    Выполните приведенную ниже инструкцию.

    ```sql
    EXEC sp_configure 'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    GO
    ```

   Например, можно выполнить предыдущую команду с `sqlcmd`. В следующем примере показано подключение к конечной точке главной реплики и выполнение скрипта. Замените значения в скрипте значениями для своей среды.

   ```bash
   sqlcmd -S <IP address>,1533 -U <user name> -P <password> -Q "EXEC sp_configure 'external scripts enabled', 1; RECONFIGURE WITH OVERRIDE;"
   ```

   Повторите этот шаг для каждой реплики.

### <a name="demonstration"></a>Демонстрация

Этот процесс показан на следующем рисунке.

[![](media/machine-learning-services/example-kube-enable-scripts.png "Demonstrate enable feature on Kubernetes")](media/machine-learning-services/example-kube-enable-scripts.png#lightbox)

Теперь все готово для выполнения скриптов Python и R в главном экземпляре кластеров больших данных. Перед тем как запустить первый скрипт, ознакомьтесь с краткими руководствами в разделе [Следующие шаги](#next-steps).

### <a name="delete-the-master-replica-endpoints"></a>Удаление конечных точек главной реплики

В кластере Kubernetes удалите конечную точку для каждой реплики. Конечная точка предоставляется в Kubernetes в качестве службы балансировки нагрузки.

Следующая команда удаляет службу балансировки нагрузки.

`kubectl delete svc <load-balancer-name> -n mssql-cluster`

Для примеров в этой статье выполните следующие команды.

```bash
kubectl delete svc mymaster-0 -n mssql-cluster
kubectl delete svc mymaster-1 -n mssql-cluster
kubectl delete svc mymaster-2 -n mssql-cluster
```

## <a name="next-steps"></a>Дальнейшие действия

+ [Краткое руководство. Создание и выполнение простых сценариев Python с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-python-create-script.md)
+ [Краткое руководство. Создание и оценка модели прогнозов в Python с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-python-train-score-model.md)
+ [Краткое руководство. Создание и выполнение простых скриптов R с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-r-create-script.md)
+ [Краткое руководство. Создание и оценка модели прогнозов в R с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-r-train-score-model.md)
