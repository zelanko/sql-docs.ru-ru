---
title: Что такое пул носителей?
titleSuffix: SQL Server big data clusters
description: Сведения о роли пула носителей SQL Server в кластере больших данных SQL Server 2019, а также архитектуре и функциональных возможностях пула носителей SQL.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fd7a38d555cbf6e2f64743f0907fbfbbdec4d41f
ms.sourcegitcommit: 6f49804b863fed44968ea5829e2c26edc5988468
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87806501"
---
# <a name="what-is-the-storage-pool-big-data-clusters-2019"></a>Что такое пул носителей ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается роль *пула носителей SQL Server* в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула носителей SQL.

## <a name="storage-pool-architecture"></a>Архитектура пула носителей

Пул носителей формируется из узлов хранилища, состоящих из SQL Server в Linux, Spark и HDFS. Все узлы хранилища в кластере больших данных SQL входят в кластер HDFS.

![Архитектура пула носителей](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Обязанности

Узлы хранилища предназначены для выполнения следующих задач:

- прием данных через Spark;
- Хранение данных в HDFS (Parquet и текстовый формат с разделителями). HDFS также обеспечивает сохраняемость данных, так как данные HDFS распределены по всем узлам хранения в кластере больших данных SQL.
- доступ к данным через конечные точки HDFS и SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих ресурсах.

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
