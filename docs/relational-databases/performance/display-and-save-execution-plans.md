---
title: Отображение и сохранение планов выполнения | Документация Майкрософт
description: Сведения о том, как отображать планы выполнения и сохранять их в файл формата XML с помощью SQL Server Management Studio.
ms.custom: ''
ms.date: 08/21/2017
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
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 19c0cee8d1ff56167032f7a0ff918b3adee24056
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457301"
---
# <a name="display-and-save-execution-plans"></a>Отображение и сохранение планов выполнения
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
В этом разделе объясняется, как отображать планы выполнения и как сохранять их в файл формата XML в среде Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Планы выполнения служат для графического отображения методов получения данных, выбранных оптимизатором запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Планы выполнения представляют стоимость выполнения определенных инструкций и запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде значков, а не таблиц, формируемых с помощью инструкций [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) и [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Графический подход полезен для понимания характеристик производительности запроса.  

Хотя оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует только один план выполнения, существуют понятия **расчетного** плана выполнения и **фактического** плана выполнения.
-  [Расчетный план выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md) возвращает план выполнения, созданный оптимизатором запросов во время компиляции. При формировании расчетного плана выполнения не выполняется никаких запросов или пакетов, поэтому расчетный план выполнения не содержит сведений времени выполнения, таких как фактические метрики использования ресурса и предупреждения времени выполнения. 
-  [Фактический план выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md) возвращает план выполнения, созданный с помощью оптимизатора запросов, после завершения выполнения запросов или пакетов. Этот план включает сведения времени выполнения, такие как метрики использования ресурса и предупреждения времени выполнения.  

Дополнительные сведения о планах выполнения запросов см. в статье [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Отображение предполагаемого плана выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Отображение действительного плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
-   [Сохранение плана выполнения в формате XML](../../relational-databases/performance/save-an-execution-plan-in-xml-format.md)  
  
  
