---
title: Что такое пулы вычислительных?
titleSuffix: SQL Server big data clusters
description: В этой статье описывается пул вычислительных в кластере SQL Server 2019 больших данных (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6da6e2b948027446623e47a58670e44cd99886de
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729158"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Что такое вычислительных пулов в кластер SQL Server больших данных?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается роль *пулов вычислений SQL Server* в кластере SQL Server 2019 предварительного просмотра больших данных. Вычислительные пулы обеспечивают горизонтальное масштабирование вычислительных ресурсов для кластера больших данных. Архитектура и функциональные возможности пул вычислительных в следующих разделах.

## <a name="compute-pool-architecture"></a>Архитектура пула вычислений

Пул вычислительных состоит из одного или нескольких вычислительных модулями, запущенными в Kubernetes. Автоматическое создание и управление этих модулей координируется [главного экземпляра SQL Server](concept-master-instance.md). Каждый модуль содержит набор базовых служб и экземпляра компонента SQL Server database engine.

## <a name="scale-out-groups"></a>Масштабируемые группы

Пул вычислительных может выступать в качестве группы горизонтального масштабирования PolyBase для распределенных запросов для различных источников данных — например, HDFS, Oracle, MongoDB или Terradata. С помощью вычислений POD, содержащихся в Kubernetes, больших данных кластеров можно автоматизировать создание и Настройка модулей POD вычислений для группы горизонтального масштабирования PolyBase.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. следующие ресурсы:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
- [Семинар: Кластерами больших данных Microsoft SQL Server архитектуры](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
