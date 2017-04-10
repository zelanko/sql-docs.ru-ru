---
title: "Неподдерживаемые функции служб Analysis Services в SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Обратная совместимость служб Analysis Services"
  - "Обратная совместимость служб SSAS"
  - "Обратная совместимость служб SQL Server Analysis Services"
  - "неподдерживаемые функции [службы Analysis Services]"
  - "неподдерживаемые возможности [службы Analysis Services]"
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
caps.latest.revision: 43
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 43
---
# Неподдерживаемые функции служб Analysis Services в SQL Server 2016
  *Неподдерживаемой* называется функция, которая больше не поддерживается. Она может быть также физически удалена из продукта. Следующие функции в [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] больше не поддерживаются.  
  
|||  
|-|-|  
|**Компонент**|**Замена или решение**|  
|[CalculationPassValue (многомерные выражения)](../mdx/calculationpassvalue-mdx.md)|Нет. Эта функция устарела в SQL Server 2005.|  
|[CalculationCurrentPass (многомерные выражения)](../mdx/calculationcurrentpass-mdx.md)|Нет. Эта функция устарела в SQL Server 2005.|  
|Подсказка оптимизатора запросов NON_EMPTY_BEHAVIOR|Нет. Эта функция устарела в SQL Server 2008.|  
|Сборки COM|Нет. Эта функция устарела в SQL Server 2008.|  
|Внутреннее свойство ячейки CELL_EVALUATION_LIST|Нет. Эта функция устарела в SQL Server 2005.|  
  
> [!NOTE]  
>  Предыдущие объявления нерекомендуемых функций из [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] остаются в силе. Так как код поддержки этих функций еще не удален из продукта, многие из них все еще присутствуют в данной версии. Хотя объявленные ранее нерекомендуемыми функции могут быть доступны, они все равно считаются таковыми и могут быть физически удалены из продукта в любой момент в ходе выпуска [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Настоятельно рекомендуется избегать использования нерекомендуемых функций во всех новых моделях и приложениях на основе [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## См. также  
 [Analysis Services Backward Compatibility](../analysis-services/analysis-services-backward-compatibility.md)   
 [Нерекомендуемые функции служб Analysis Services в SQL Server 2016](../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md)  
  
  