---
title: Мониторинг приложений с помощью azdata и панели мониторинга Grafana
titleSuffix: SQL Server Big Data Clusters
description: Мониторинг приложений с помощью azdata и Grafana в кластере больших данных SQL Server 2019.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 08/16/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1391b88f2762293aa4eebf255682605bf5b6b1e0
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257284"
---
# <a name="monitor-applications-with-azdata-and-grafana-dashboard"></a>Мониторинг приложений с помощью azdata и панели мониторинга Grafana

Grafana — это одно из лучших облачных средств виртуализации, которые можно использовать для предоставления различных метрик мониторинга приложения, работающего в Kubernetes.  

В этой статье описывается мониторинг приложений в кластерах больших данных SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- [Кластер больших данных SQL Server 2019](deployment-guidance.md)
- [[!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)]](../azdata/install/deploy-install-azdata.md)

## <a name="capabilities"></a>Возможности

В SQL Server 2019 можно создать, удалить, описать, инициализировать, перечислить, запустить и обновить приложение. В следующей таблице описаны команды развертывания приложения, которые можно использовать с **azdata**.

|Get-Help |Описание |
|:---|:---|
|`azdata bdc endpoint list` | Список конечных точек для кластера больших данных. |


Следующий пример можно использовать для перечисления конечной точки **панели мониторинга Grafana**:

```bash
azdata bdc endpoint list --endpoint-name metricsui 
```

В выходных данных будет предоставлена конечная точка, в которой можно использовать имя пользователя и пароль для входа в кластер. 

![Панель мониторинга Grafana](media/big-data-cluster-monitor-apps/grafana-dashboard-endpoint.png)


Открыв панель мониторинга, перейдите в раздел  **Метрики ведущих приложений**, где вы получите более подробные сведения о приложении и сможете следить за ним.  

![Метрики ведущих приложений](media/big-data-cluster-monitor-apps/host-apps-metrics.png)


Чтобы узнать больше о единственном модуле Pod приложения (в некоторых случаях у вас есть несколько копий приложения), перейдите в раздел  **Метрики ведущих модулей**  и выберите нужный модуль Pod. Просмотреть метрики можно следующим образом:  

![Метрики ведущих модулей Pod](media/big-data-cluster-monitor-apps/host-pods-metrics.png) 


## <a name="next-steps"></a>Дальнейшие шаги

Дополнительные примеры можно просмотреть в наборе [примеров развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).