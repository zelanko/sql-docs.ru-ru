---
title: Что такое вычислительные пулы
titleSuffix: SQL Server big data clusters
description: В этой статье описывается вычислительный пул в кластере больших данных SQL Server 2019 (предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d9ae112369ddad91bec125ec19713040a5aae915
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958801"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Что такое вычислительные пулы в кластере больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается назначение *вычислительных пулов SQL Server* в кластере больших данных предварительной версии SQL Server 2019. Вычислительные пулы обеспечивают горизонтальное масштабирование вычислительных ресурсов для кластера больших данных. В следующих разделах содержатся сведения об архитектуре и функциональных возможностях вычислительного пула.

## <a name="compute-pool-architecture"></a>Архитектура вычислительного пула

Вычислительный пул состоит из одного или нескольких вычислительных объектов pod, работающих в Kubernetes. Автоматическое создание этих объектов и управление ими координируется [главным экземпляром SQL Server](concept-master-instance.md). Каждый объект pod содержит набор базовых служб и экземпляр ядра СУБД SQL Server.

## <a name="scale-out-groups"></a>Масштабируемые группы

Вычислительный пул может выступать в роли масштабируемой группы PolyBase для распределенных запросов к различным источникам данных, таким как HDFS, Oracle, MongoDB или Terradata. Kubernetes позволяет автоматизировать создание и настройку вычислительных объектов pod в кластерах больших данных для масштабируемых групп PolyBase.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server см. в следующих статьях:

- [Что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md)
- [Семинар. Архитектура кластеров больших данных Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
