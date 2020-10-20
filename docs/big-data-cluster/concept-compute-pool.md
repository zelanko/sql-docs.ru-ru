---
title: Что такое вычислительные пулы
titleSuffix: SQL Server big data clusters
description: В этой статье описывается вычислительный пул в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 10/15/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9c3374b0820233e20ee73b85947ed2b8a61847c0
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866804"
---
# <a name="what-are-compute-pools-sql-server-big-data-clusters"></a>Что такое вычислительные пулы в кластерах больших данных SQL Server?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается назначение *вычислительных пулов SQL Server* в кластерах больших данных SQL Server. Вычислительные пулы обеспечивают горизонтальное масштабирование вычислительных ресурсов для кластера больших данных. Они используются для разгрузки главного экземпляра SQL Server, беря на себя вычислительные операции или промежуточные результирующие наборы. В следующих разделах содержатся сведения об архитектуре, функциональных возможностях и сценариях использования вычислительного пула.

Вы также можете просмотреть это пятиминутное видео для ознакомления с вычислительными пулами:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Compute-Pool/player?WT.mc_id=dataexposed-c9-niner]

## <a name="compute-pool-architecture"></a>Архитектура вычислительного пула

Вычислительный пул состоит из одного или нескольких вычислительных объектов pod, работающих в Kubernetes. Автоматическое создание этих объектов и управление ими координируется [главным экземпляром SQL Server](concept-master-instance.md). Каждый объект pod содержит набор базовых служб и экземпляр ядра СУБД SQL Server.

![Архитектура вычислительного пула](media/concept-compute-pool/compute-pool-architecture.png)

## <a name="scale-out-groups"></a>Масштабируемые группы

Вычислительный пул может выступать в роли группы горизонтального увеличения масштаба PolyBase для распределенных запросов к внешним источникам данных, таким как SQL Server, Oracle, MongoDB, Teradata или HDFS. Kubernetes позволяет автоматизировать создание и настройку вычислительных объектов pod в кластерах больших данных для групп горизонтального увеличения масштаба PolyBase.

## <a name="compute-pool-scenarios"></a>Сценарии использования вычислительных пулов

Ниже перечислены сценарии, в которых используется вычислительный пул:

- Когда запросы, отправленные в главный экземпляр, используют одну или несколько таблиц, расположенных в [пуле носителей](concept-storage-pool.md).

- Когда запросы, отправленные в главный экземпляр, используют одну или несколько таблиц с циклическим распределением, расположенных в [пуле данных](concept-data-pool.md).

- Когда запросы, отправленные в главный экземпляр, используют **секционированные** таблицы с внешними источниками данных (SQL Server, Oracle, MongoDB и Teradata). В этом сценарии должно быть включено указание запроса OPTION (FORCE SCALEOUTEXECUTION).

- Когда запросы, отправленные в главный экземпляр, используют одну или несколько таблиц, расположенных в [HDFS Tiering](hdfs-tiering.md).

Ниже перечислены сценарии, в которых **не** используется вычислительный пул:

- Когда запросы, отправленные в главный экземпляр, используют одну или несколько таблиц во внешнем кластере Hadoop HDFS.

- Когда запросы, отправленные в главный экземпляр, используют одну или несколько таблиц в Хранилище BLOB-объектов Azure.

- Когда запросы, отправленные в главный экземпляр, используют **несекционированные** таблицы с внешними источниками данных (SQL Server, Oracle, MongoDB и Teradata).

- Когда включено указание запроса OPTION (DISABLE SCALEOUTEXECUTION).

- Когда запросы, отправленные в главный экземпляр, применяются к базам данных, расположенным в главном экземпляре.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих ресурсах.

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
