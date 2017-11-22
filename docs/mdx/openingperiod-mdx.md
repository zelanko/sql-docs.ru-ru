---
title: "OpeningPeriod (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: OPENINGPERIOD
dev_langs: kbMDX
helpviewer_keywords: OpeningPeriod function
ms.assetid: bebf55cf-e5c6-42b1-98f2-1d6e54093d4c
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 338ca8f96edd6204e07786c1b4d10195ce180326
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также:  
 [TopCount &#40; Многомерные Выражения &#41;](../mdx/topcount-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40; Многомерные Выражения &#41;](../mdx/firstsibling-mdx.md)  
  
  
