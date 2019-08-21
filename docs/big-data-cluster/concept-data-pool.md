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
ms.openlocfilehash: bfd4d9d6ca24599a2297799555f53a83c6601420
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652267"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Что такое пулы данных в кластере больших данных SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается роль *SQL Server пулов данных* в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула данных SQL.

## <a name="data-pool-architecture"></a>Архитектура пула данных

Пул данных состоит из одного или нескольких экземпляров пула данных SQL Server. Экземпляры пула данных SQL предоставляют постоянное хранилище SQL Server для кластера. Пул данных используется для приема данных из SQL-запросов или заданий Spark. Чтобы улучшить производительность в крупных наборах данных, данные в пуле данных распределяются сегментами по экземпляру пула данных SQL участника.

## <a name="scale-out-data-marts"></a>Киоски данных горизонтального масштабирования

Пулы данных позволяют создавать киоски данных горизонтального масштабирования, где внешние данные из нескольких источников принимаются в пул данных. Так как данные распределяются между экземплярами пула данных, параллельные запросы к проверенным данным более эффективны.

![Киоск данных горизонтального масштабирования](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]см. в следующих ресурсах:

- [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]Что?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
