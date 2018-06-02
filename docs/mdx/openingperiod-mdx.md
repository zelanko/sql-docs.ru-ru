---
title: OpeningPeriod (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9384a2993423c68db1d65a92cb0b532502c110b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581366"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает первый элемент с общим родителем из потомков заданного уровня, необязательно заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Эта функция прежде всего предназначена для использования в измерении времени, но может быть использована и для других измерений.  
  
-   Если выражение уровня указано, **OpeningPeriod** функция использует иерархию, содержащую заданный уровень и возвращает первый элемент среди потомков элемента по умолчанию на заданном уровне.  
  
-   Если указано выражение уровня и выражение элемента, **OpeningPeriod** функция возвращает первый элемент среди потомков заданного элемента на заданном уровне внутри иерархии, содержащей указанный уровень.  
  
-   Если ни выражение уровня, ни выражение элемента не указано, **OpeningPeriod** функция использует уровень по умолчанию и элемент из измерения типа Time.  
  
> [!NOTE]  
>  [ClosingPeriod](../mdx/closingperiod-mdx.md) функция подобна **OpeningPeriod** за тем исключением, которое **ClosingPeriod** функция возвращает последнего родственника вместо первого такого элемента.  
  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;многомерных Выражений&#41;](../mdx/firstsibling-mdx.md)  
  
  
