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
ms.openlocfilehash: 114296d0bad77c3bbbb088feed13bd6a4bd5a074
ms.sourcegitcommit: 594cee116fa4ee321e1f5e5206f4a94d408f1576
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70009330"
---
# <a name="what-is-the-storage-pool-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Что такое пул носителей ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается роль *пула носителей SQL Server* в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула носителей SQL.

## <a name="storage-pool-architecture"></a>Архитектура пула носителей

Пул носителей формируется из узлов хранилища, состоящих из SQL Server в Linux, Spark и HDFS. Все узлы хранилища в кластере больших данных SQL входят в кластер HDFS.

![Архитектура пула носителей](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Функции узлов

Узлы хранилища предназначены для выполнения следующих задач:

- прием данных через Spark;
- Хранение данных в HDFS (Parquet и текстовый формат с разделителями). HDFS также обеспечивает сохраняемость данных, так как данные HDFS распределены по всем узлам хранения в кластере больших данных SQL.
- доступ к данным через конечные точки HDFS и SQL Server.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]см. в следующих ресурсах:

- [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]Что?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
