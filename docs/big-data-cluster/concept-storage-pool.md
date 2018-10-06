---
title: Что такое пул носителей кластеров SQL Server больших данных? | Документы Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 100ce09f7066a6df33d7b1daaf50db50bda4ed03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796315"
---
# <a name="what-is-the-sql-server-big-data-clusters-storage-pool"></a>Что такое пул носителей кластеров SQL Server больших данных?

В этой статье описывается роль *пул носителей для SQL Server* в SQL Server 2019 preview кластера больших данных. В следующих разделах об архитектуре и функциях SQL пула носителей.

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
