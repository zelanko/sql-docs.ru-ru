---
title: Что такое пулы данных?
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье описывается пула данных в кластере SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: c3df07da100bf0bbfc0b2238cb4154b4c3a363e3
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241615"
---
# <a name="what-are-data-pools-in-a-sql-server-2019-big-data-cluster"></a>Что такое пулы данных в кластере SQL Server 2019 больших данных?

В этой статье описывается роль *пулы данных SQL Server* в кластере SQL Server 2019 больших данных (Предварительная версия). Архитектура и функциональные возможности пула данных SQL в следующих разделах.

## <a name="data-pool-architecture"></a>Архитектура пула данных

Пул данных состоит из одного или нескольких экземпляров пула данных SQL Server. Экземпляры пула данных SQL обеспечивают постоянное хранилище SQL Server для кластера. Пул данных используется для приема данных из SQL-запросы или заданий Spark. Для повышения быстродействия больших наборов данных, данные в пуле данных распределяются на сегменты по экземплярам пула данных члена SQL.

## <a name="scale-out-data-marts"></a>Киоски данных горизонтального масштабирования

Пулы данных позволяют создавать киоски данных горизонтального масштабирования, где принимаются внешние данные из нескольких источников в пул данных. Так как данные распределяются между экземплярами пула данных, параллельные запросы к отобранные данные являются более эффективными.

![Киоск данных горизонтального масштабирования](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. в разделе приведены общие:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
