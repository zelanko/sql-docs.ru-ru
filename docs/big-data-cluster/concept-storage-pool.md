---
title: Что такое пул носителей кластеров SQL Server больших данных? | Документы Майкрософт
description: В этой статье описывается пула носителей в кластер SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: cbf9ff14ece1b33e1c271786bc96f0ac590b807e
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050756"
---
# <a name="what-is-the-sql-server-big-data-clusters-storage-pool"></a>Что такое пул носителей кластеров SQL Server больших данных?

В этой статье описывается роль *пул носителей для SQL Server* в кластере SQL Server 2019 предварительного просмотра больших данных. В следующих разделах об архитектуре и функциях SQL пула носителей.

## <a name="storage-pool-architecture"></a>Архитектура хранилища пула

Пул носителей состоит из хранилища, которые узлы состоит из SQL Server в Linux, Spark и HDFS. Все узлы хранилища в кластере SQL больших данных являются членами кластера HDFS.

![Архитектура хранилища пула](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Обязанности

Узлы хранилища отвечают за:

- Прием данных через Spark.
- Хранилище данных в HDFS (формат Parquet). HDFS также представлена сохранение данных HDFS данные распределяются на всех узлах хранилища в кластере SQL больших данных.
- Доступ к данным через конечные точки HDFS и SQL Server.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. в разделе приведены общие:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
