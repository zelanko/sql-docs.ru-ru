---
title: ClosingPeriod (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c6c9dea03a4b09ae4dcbe66e6712a542b1920ce0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181582"
---
# <a name="closingperiod-mdx"></a>ClosingPeriod (многомерные выражения)


  Возвращает последний элемент среди потомков указанного элемента на указанном уровне.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ClosingPeriod( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Эта функция прежде всего предназначена для использования в измерении времени, но может быть использована и для других измерений.  
  
-   Если выражение уровня указано, **ClosingPeriod** функция использует измерение, содержащее заданный уровень и возвращает последний элемент среди потомков элемента по умолчанию на заданном уровне.  
  
-   Если выражение уровня и выражение элемента, **ClosingPeriod** функция возвращает последний элемент среди потомков заданного элемента на заданном уровне.  
  
-   Если ни выражение уровня, ни выражение элемента указано, **ClosingPeriod** функция использует уровень по умолчанию и элемент из измерения (если таковые имеются) в кубе времени.  
  
 **ClosingPeriod** функция эквивалентна следующей инструкции многомерных Выражений:  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`.  
  
> [!NOTE]  
>  [OpeningPeriod](../mdx/openingperiod-mdx.md) функция аналогична **ClosingPeriod** за тем исключением, которое **OpeningPeriod** функция возвращает первый родственный элемент вместо последнего того же уровня.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается значение меры по умолчанию для элемента FY2007 измерения Date (измерение времени). Этот элемент возвращается, поскольку уровень Fiscal Year — первый потомок уровня «Все». Иерархия Fiscal — иерархия по умолчанию, поскольку это первая пользовательская иерархия из коллекции иерархий. Элемент FY 2007 — последний элемент этой иерархии данного уровня.  
  
```  
SELECT ClosingPeriod() ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента «30 ноября 2006» уровня Date.Date.Date в иерархии атрибута Date.Date. Это последний элемент уровня «Все» в иерархии атрибута Date.Date.  
  
```  
SELECT ClosingPeriod ([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента December 2003, который является последним элементом из потомков элемента «2003» на уровне года в пользовательской иерархии Calendar.  
  
```  
SELECT ClosingPeriod ([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента June 2003, который является последним элементом из потомков элемента «2003» на уровне года в пользовательской иерархии Fiscal.  
  
```  
SELECT ClosingPeriod ([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [OpeningPeriod &#40;многомерных Выражений&#41;](../mdx/openingperiod-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40;многомерных Выражений&#41;](../mdx/lastsibling-mdx.md)  
  
  
