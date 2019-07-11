---
title: Что такое пулы данных?
titleSuffix: SQL Server big data clusters
description: В этой статье описывается пула данных в кластере SQL Server 2019 больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7530036cae939f6fd5d45fb5575f2161a36f21a1
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729127"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Что такое пулы данных в кластере SQL Server больших данных?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается роль *пулы данных SQL Server* в кластере SQL Server 2019 больших данных (Предварительная версия). Архитектура и функциональные возможности пула данных SQL в следующих разделах.

## <a name="data-pool-architecture"></a>Архитектура пула данных

Пул данных состоит из одного или нескольких экземпляров пула данных SQL Server. Экземпляры пула данных SQL обеспечивают постоянное хранилище SQL Server для кластера. Пул данных используется для приема данных из SQL-запросы или заданий Spark. Для повышения быстродействия больших наборов данных, данные в пуле данных распределяются на сегменты по экземплярам пула данных члена SQL.

## <a name="scale-out-data-marts"></a>Киоски данных горизонтального масштабирования

Пулы данных позволяют создавать киоски данных горизонтального масштабирования, где принимаются внешние данные из нескольких источников в пул данных. Так как данные распределяются между экземплярами пула данных, параллельные запросы к отобранные данные являются более эффективными.

![Киоск данных горизонтального масштабирования](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. следующие ресурсы:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
- [Семинар: Кластерами больших данных Microsoft SQL Server архитектуры](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
