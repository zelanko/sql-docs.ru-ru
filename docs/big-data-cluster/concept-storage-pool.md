---
title: Что такое пул носителей?
titleSuffix: SQL Server big data clusters
description: В этой статье описывается пул носителей в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 58e6f16a088d6dc6c1fc6bd32297e7bd698acbbf
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958651"
---
# <a name="what-is-the-storage-pool-sql-server-big-data-clusters"></a>Что такое пул носителей (в кластере больших данных SQL Server)?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается роль *пула носителей SQL Server* в кластере больших данных SQL Server 2019 (предварительная версия). В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула носителей SQL.

## <a name="storage-pool-architecture"></a>Архитектура пула носителей

Пул носителей формируется из узлов хранилища, состоящих из SQL Server в Linux, Spark и HDFS. Все узлы хранилища в кластере больших данных SQL входят в кластер HDFS.

![Архитектура пула носителей](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Функции узлов

Узлы хранилища предназначены для выполнения следующих задач:

- прием данных через Spark;
- хранение данных в HDFS (формат Parquet). HDFS также обеспечивает сохраняемость данных, так как данные HDFS распределены по всем узлам хранения в кластере больших данных SQL.
- доступ к данным через конечные точки HDFS и SQL Server.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server см. в следующих статьях:

- [Что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md)
- [Семинар. Архитектура кластеров больших данных Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
