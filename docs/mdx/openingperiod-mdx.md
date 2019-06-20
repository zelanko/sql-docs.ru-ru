---
title: OpeningPeriod (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01144d6a82319b7853ae60f901a5fc0ad3c78d6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63277960"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (многомерные выражения)


  Возвращает первый элемент с общим родителем из потомков заданного уровня, необязательно заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Эта функция прежде всего предназначена для использования в измерении времени, но может быть использована и для других измерений.  
  
-   Если выражение уровня указано, **OpeningPeriod** функция использует иерархию, содержащую заданный уровень и возвращает первый родственный элемент среди потомков элемента по умолчанию на заданном уровне.  
  
-   Если выражение уровня и выражение элемента, **OpeningPeriod** функция возвращает первый родственный элемент среди потомков заданного элемента на заданном уровне внутри иерархии, содержащей указанный уровень.  
  
-   Если ни выражение уровня, ни выражение элемента не заданы, **OpeningPeriod** функция использует уровень по умолчанию и элемент из измерения типа Time.  
  
> [!NOTE]  
>  [ClosingPeriod](../mdx/closingperiod-mdx.md) функция аналогична **OpeningPeriod** за тем исключением, которое **ClosingPeriod** функция возвращает последний элемент вместо первого того же уровня.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается значение меры по умолчанию для элемента FY2002 измерения Date (измерение времени). Этот элемент возвращается, поскольку уровень Fiscal Year — первый потомок уровня «Все». Иерархия Fiscal — иерархия по умолчанию, поскольку это первая пользовательская иерархия из коллекции иерархий. Элемент FY2002 — первый элемент этой иерархии данного уровня.  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента «1 июля 2001» уровня Date.Date.Date в иерархии атрибута Date.Date. Это первый элемент уровня «Все» в иерархии атрибута Date.Date.  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента January 2003, который является первым элементом из потомков элемента «2003» на уровне года в пользовательской иерархии Calendar.  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента July 2003, который является первым элементом из потомков элемента «2003» на уровне года в пользовательской иерархии Fiscal.  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [TopCount &#40;многомерных Выражений&#41;](../mdx/topcount-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;многомерных Выражений&#41;](../mdx/firstsibling-mdx.md)  
  
  
