---
title: Что такое пулы данных?
titleSuffix: SQL Server big data clusters
description: Сведения о роли пула данных SQL Server в кластере больших данных SQL Server, а также архитектуре и функциональных возможностях пула данных SQL.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4d9eaba636c2567d60dfc62ce37080717e9c32e9
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680579"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Что такое пулы данных в кластере больших данных SQL Server?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

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
