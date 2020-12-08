---
title: Сравнение и анализ планов выполнения | Документация Майкрософт
description: Сведения о том, как сравнивать и анализировать планы выполнения с помощью среды SQL Server Management Studio. Планы выполнения служат для отображения методов получения данных, используемых оптимизатором запросов.
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: wiassaf
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 9a969277322f24861e2dcd4c85e92df9e4ebb4f0
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505368"
---
# <a name="compare-and-analyze-execution-plans"></a>Сравнение и анализ планов выполнения
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
В этом разделе объясняется, как сравнивать и анализировать планы выполнения с помощью Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Эта функция доступна начиная с [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] версии 17.4.  
  
Планы выполнения служат для графического отображения методов получения данных, выбранных оптимизатором запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Планы выполнения представляют стоимость выполнения определенных инструкций и запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде значков, а не таблиц, формируемых с помощью инструкций [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) и [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Графический подход очень полезен для понимания характеристик производительности запроса. 

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит функции, которые позволяют пользователям сравнивать два плана выполнения, например предположительно хорошие и плохие планы для одного запроса, и выполнять анализ основных причин. Кроме того, существует возможность выполнять анализ плана одного запроса, получая ценные сведения о сценариях, которые могут влиять на производительность этого запроса.

Дополнительные сведения о плане выполнения запроса см. в описании [предполагаемого плана выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md), [фактического плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md), а также в [руководстве по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>в этом разделе  
[Сравнение планов выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md)     
[Анализ фактического плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md)      
  
