---
title: This (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77db403ee016283a565a6bc86d2f6857de0eff45
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743253"
---
# <a name="this-mdx"></a>This (многомерные выражения)


  Возвращает текущий вложенный куб для использования в назначениях в скрипте вычисления многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Вычисления](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
