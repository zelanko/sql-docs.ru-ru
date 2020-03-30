---
title: Сравнение и анализ планов выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
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
ms.openlocfilehash: 4b300d1fbc144f25b3f725f34e49d961953c434c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72289339"
---
# <a name="compare-and-analyze-execution-plans"></a>Сравнение и анализ планов выполнения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В этом разделе объясняется, как сравнивать и анализировать планы выполнения с помощью Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Эта функция доступна начиная с [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] версии 17.4.  
  
Планы выполнения служат для графического отображения методов получения данных, выбранных оптимизатором запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Планы выполнения представляют стоимость выполнения определенных инструкций и запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде значков, а не таблиц, формируемых с помощью инструкций [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) и [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Графический подход очень полезен для понимания характеристик производительности запроса. 

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит функции, которые позволяют пользователям сравнивать два плана выполнения, например предположительно хорошие и плохие планы для одного запроса, и выполнять анализ основных причин. Кроме того, существует возможность выполнять анализ плана одного запроса, получая ценные сведения о сценариях, которые могут влиять на производительность этого запроса.

Дополнительные сведения о плане выполнения запроса см. в описании [предполагаемого плана выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md), [фактического плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md), а также в [руководстве по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>в этом разделе  
[Сравнение планов выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md)     
[Анализ фактического плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md)      
  
