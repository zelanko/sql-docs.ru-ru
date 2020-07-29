---
title: Что такое вычислительные пулы
titleSuffix: SQL Server big data clusters
description: В этой статье описывается вычислительный пул в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c7afce300e40f6703cbe4c2d734751aa27256959
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730669"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Что такое вычислительные пулы в кластере больших данных SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается назначение *пулов вычислений SQL Server* в кластере больших данных SQL Server. Вычислительные пулы обеспечивают горизонтальное масштабирование вычислительных ресурсов для кластера больших данных. В следующих разделах содержатся сведения об архитектуре и функциональных возможностях вычислительного пула.

Вы также можете просмотреть это пятиминутное видео для ознакомления с вычислительными пулами:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Compute-Pool/player?WT.mc_id=dataexposed-c9-niner]


## <a name="compute-pool-architecture"></a>Архитектура вычислительного пула

Вычислительный пул состоит из одного или нескольких вычислительных объектов pod, работающих в Kubernetes. Автоматическое создание этих объектов и управление ими координируется [главным экземпляром SQL Server](concept-master-instance.md). Каждый объект pod содержит набор базовых служб и экземпляр ядра СУБД SQL Server.

## <a name="scale-out-groups"></a>Масштабируемые группы

Пул вычислений может выступать в роли масштабируемой группы PolyBase для распределенных запросов к различным источникам данных, таким как HDFS, Oracle, MongoDB или Teradata. Kubernetes позволяет автоматизировать создание и настройку вычислительных объектов pod в кластерах больших данных для масштабируемых групп PolyBase.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих ресурсах.

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
