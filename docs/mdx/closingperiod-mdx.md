---
title: ClosingPeriod (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 102485ede0e52389d43bdb64742a2564aaa71419
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016791"
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
  
## <a name="remarks"></a>Remarks  
 Эта функция прежде всего предназначена для использования в измерении времени, но может быть использована и для других измерений.  
  
-   Если выражение уровня задано, функция **ClosingPeriod** использует измерение, которое содержит указанный уровень, и возвращает последний элемент среди потомков элемента по умолчанию на заданном уровне.  
  
-   Если указаны как выражение уровня, так и выражение элемента, функция **ClosingPeriod** Возвращает последний элемент того же уровня среди потомков указанного элемента на заданном уровне.  
  
-   Если не указано ни выражение уровня, ни выражение элемента, функция **ClosingPeriod** использует уровень по умолчанию и элемент измерения (если таковые имеются) в Кубе с типом времени.  
  
 Функция **ClosingPeriod** эквивалентна следующей инструкции многомерных выражений:  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`.  
  
> [!NOTE]  
>  Функция [OpeningPeriod](../mdx/openingperiod-mdx.md) похожа на функцию **ClosingPeriod** , за исключением того, что функция **OpeningPeriod** возвращает первый элемент того же уровня, а не последний элемент того же уровня.  
  
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
  
## <a name="see-also"></a>См. также:  
 [OpeningPeriod &#40;&#41;многомерных выражений](../mdx/openingperiod-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40;&#41;многомерных выражений](../mdx/lastsibling-mdx.md)  
  
  
