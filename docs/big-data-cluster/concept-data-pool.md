---
title: Что такое пулы данных?
titleSuffix: SQL Server big data clusters
description: В этой статье описан пул данных в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6fdcaf7e54455d40cd3bcdb8c6ec1a1ec3bf75f7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253134"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Что такое пулы данных в кластере больших данных SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описана роль *пулов данных SQL Server* в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула данных SQL.

В этом пятиминутном видео содержатся общие сведения о пулах данных, а также показано, как запрашивать данные из пулов данных.

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Querying-Data-from-Big-Data-Cluster-Data-Pool/player?WT.mc_id=dataexposed-c9-niner]

## <a name="data-pool-architecture"></a>Архитектура пула данных

Пул данных состоит из одного или нескольких экземпляров пула данных SQL Server. Экземпляры пула данных SQL предоставляют постоянное хранилище SQL Server для кластера. Пул данных используется для приема данных из SQL-запросов или заданий Spark. Чтобы улучшить производительность в крупных наборах данных, данные в пуле данных распределяются сегментами по экземпляру пула данных SQL участника.

## <a name="scale-out-data-marts"></a>Киоски данных горизонтального масштабирования

Пулы данных позволяют создавать киоски данных горизонтального масштабирования, где внешние данные из нескольких источников принимаются в пул данных. Так как данные распределяются между экземплярами пула данных, параллельные запросы к проверенным данным более эффективны.

![Киоск данных горизонтального масштабирования](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих ресурсах.

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
