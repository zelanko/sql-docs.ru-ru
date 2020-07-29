---
title: Что такое пул носителей?
titleSuffix: SQL Server big data clusters
description: В этой статье описывается пул носителей в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7a9d3e9e16eb923e0954154b46362cdc88c0bff
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730693"
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
