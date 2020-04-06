---
title: Службы машинного обучения (Python, R)
titleSuffix: SQL Server Big Data Clusters
description: Узнайте, как выполнять скрипты Python и R в главном экземпляре кластеров больших данных SQL Server с помощью служб машинного обучения.
author: dphansen
ms.author: davidph
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
ms.openlocfilehash: dd8e1b948d259b4c233aebcb3614dea5b3e72129
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664129"
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

## <a name="enable-always-on-availability-groups"></a>Включение групп доступности AlwaysOn

При использовании кластеров больших данных SQL Server с [группами доступности Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) необходимо выполнить несколько дополнительных действий, чтобы включить службы машинного обучения.

1. Подключитесь к главному экземпляру и выполните следующую инструкцию:

    ```sql
    SELECT @@SERVERNAME
    ```

    Запишите имя сервера. В данном примере имя сервера для главного экземпляра — **master-2**.

1. В каждой реплике в группе доступности Always On в кластере больших данных выполните следующие команды `kubectl`:

    ```
    kubectl -n bdc expose pod master-0 --port=1533 --name=mymaster-0 --type=LoadBalancer

    kubectl -n bdc expose pod master-1 --port=1533 --name=mymaster-1 --type=LoadBalancer

    kubectl -n bdc expose pod master-2 --port=1533 --name=mymaster-2 --type=LoadBalancer
    ```

    Выходные данные должны иметь следующий вид:
    
    ```
    service/mymaster-0 exposed

    service/mymaster-1 exposed

    service/mymaster-2 exposed
    ```

1. Подключитесь к каждой конечной точке главной реплики и разрешите выполнение скрипта.

    Выполните приведенную ниже инструкцию.

    ```sql
    EXEC sp_configure 'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    GO
    ```

Теперь все готово для выполнения скриптов Python и R в главном экземпляре кластеров больших данных. Перед тем как запустить первый скрипт, ознакомьтесь с краткими руководствами ниже.

## <a name="next-steps"></a>Дальнейшие действия

+ [Краткое руководство. Создание и выполнение простых сценариев Python с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-python-create-script.md)
+ [Краткое руководство. Создание и оценка модели прогнозов в Python с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-python-train-score-model.md)
+ [Краткое руководство. Создание и выполнение простых скриптов R с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-r-create-script.md)
+ [Краткое руководство. Создание и оценка модели прогнозов в R с помощью служб машинного обучения SQL Server](../machine-learning/tutorials/quickstart-r-train-score-model.md)
