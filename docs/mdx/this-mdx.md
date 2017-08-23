---
title: "This (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- THIS
dev_langs:
- kbMDX
helpviewer_keywords:
- This function [MDX]
ms.assetid: 87acddee-ae54-49ee-8923-1b760606e8b7
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 54b73433950bb6e60d1262955c3f65ad0ab7413e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="this-mdx"></a>This (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает текущий вложенный куб для использования в назначениях в скрипте вычисления многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Замечания  
 **Это** функцию можно использовать вместо любого выражения вложенного куба для предоставления к текущему вложенному кубу в текущей области в скрипте вычисления многомерного Выражения. **Это** необходимо использовать функцию в левой части назначения.  
  
## <a name="examples"></a>Примеры  
 Следующий фрагмент скрипта многомерных выражений показывает, как использовать ключевое слово This с инструкциями SCOPE для назначений вложенным кубам:  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2005],`  
  
 `[Date].[Fiscal].[Fiscal Quarter].Members,`  
  
 `[Measures].[Sales Amount Quota]`  
  
 `) ;`  
  
 `This = ParallelPeriod`  
  
 `(`  
  
 `[Date].[Fiscal].[Fiscal Year], 1,`  
  
 `[Date].[Fiscal].CurrentMember`  
  
 `) * 1.35 ;`  
  
 `/*-- Allocate equally to months in FY 2002 -----------------------------*/`  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2002],`  
  
 `[Date].[Fiscal].[Month].Members`  
  
 `) ;`  
  
 `This = [Date].[Fiscal].CurrentMember.Parent / 3 ;`  
  
 `End Scope ;`  
  
 `End Scope;`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Вычисления](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  

