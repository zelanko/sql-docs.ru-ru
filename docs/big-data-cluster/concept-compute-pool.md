---
title: Что такое пулы вычислительных?
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье описывается пул вычислительных в кластере SQL Server 2019 больших данных (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d9189c6533563a44b597dddc99e263d78750aa6a
ms.sourcegitcommit: 715683b5fc7a8e28a86be8949a194226b72ac915
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477869"
---
# <a name="what-are-compute-pools-in-a-sql-server-2019-big-data-cluster"></a>Что такое пулы вычислительных в кластере SQL Server 2019 больших данных?

В этой статье описывается роль *пулов вычислений SQL Server* в кластере SQL Server 2019 предварительного просмотра больших данных. Вычислительные пулы обеспечивают горизонтальное масштабирование вычислительных ресурсов для кластера больших данных. Архитектура и функциональные возможности пул вычислительных в следующих разделах.

## <a name="compute-pool-architecture"></a>Архитектура пула вычислений

Пул вычислительных состоит из одного или нескольких вычислительных модулями, запущенными в Kubernetes. Автоматическое создание и управление этих модулей координируется [главного экземпляра SQL Server](concept-master-instance.md). Каждый модуль содержит набор базовых служб и экземпляра компонента SQL Server database engine.

## <a name="scale-out-groups"></a>Масштабируемые группы

Пул вычислительных может выступать в качестве группы горизонтального масштабирования PolyBase для распределенных запросов для различных источников данных — например, HDFS, Oracle, MongoDB или Terradata. С помощью вычислений POD, содержащихся в Kubernetes, больших данных кластеров можно автоматизировать создание и Настройка модулей POD вычислений для группы горизонтального масштабирования PolyBase.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. следующие ресурсы:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
- [Семинар: Кластерами больших данных Microsoft SQL Server архитектуры](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
