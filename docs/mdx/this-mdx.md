---
title: This (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 12455c82fe7a885a3530b6c0db216b9996a5eda6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893563"
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
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)   
 [Вычисления](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/calculations)  
  
  
