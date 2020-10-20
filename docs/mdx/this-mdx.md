---
description: This (многомерные выражения)
title: This (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b55a416a14d0b837d134e7f9d8520d77cc13e375
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192334"
---
# <a name="this-mdx"></a>This (многомерные выражения)


  Возвращает текущий вложенный куб для использования в назначениях в скрипте вычисления многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Remarks  
 **Эта** функция может использоваться вместо любого выражения вложенного куба для предоставления текущего вложенного куба в пределах текущей области скрипта вычисления многомерных выражений. **Эта** функция должна использоваться в левой части назначения.  
  
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
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-function-reference-mdx.md)   
 [Вычисления](/analysis-services/multidimensional-models-olap-logical-cube-objects/calculations)  
  
