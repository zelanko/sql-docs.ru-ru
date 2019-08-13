---
title: Что такое пулы данных?
titleSuffix: SQL Server big data clusters
description: В этой статье описан пул данных в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f9355508e4d32dd9a6152781fba325ded2fa7425
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958739"
---
# <a name="what-are-data-pools-in-a-sql-server-big-data-cluster"></a>Что такое пулы данных в кластере больших данных SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описана роль *пулов данных SQL Server* в кластере больших данных SQL Server 2019 (предварительная версия). В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула данных SQL.

## <a name="data-pool-architecture"></a>Архитектура пула данных

Пул данных состоит из одного или нескольких экземпляров пула данных SQL Server. Экземпляры пула данных SQL предоставляют постоянное хранилище SQL Server для кластера. Пул данных используется для приема данных из SQL-запросов или заданий Spark. Чтобы улучшить производительность в крупных наборах данных, данные в пуле данных распределяются сегментами по экземпляру пула данных SQL участника.

## <a name="scale-out-data-marts"></a>Киоски данных горизонтального масштабирования

Пулы данных позволяют создавать киоски данных горизонтального масштабирования, где внешние данные из нескольких источников принимаются в пул данных. Так как данные распределяются между экземплярами пула данных, параллельные запросы к проверенным данным более эффективны.

![Киоск данных горизонтального масштабирования](media/concept-data-pool/data-virtualization-improvements.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server см. в следующих статьях.

- [Что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md)
- [Семинар. Архитектура кластеров больших данных Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
