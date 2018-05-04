---
title: ClosingPeriod (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CLOSINGPERIOD
dev_langs:
- kbMDX
helpviewer_keywords:
- ClosingPeriod function
ms.assetid: ae709017-219d-43e1-a98a-a85bd365b4cd
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d53c0686742f096f49519da93e64ea2b6706d056
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="closingperiod-mdx"></a>ClosingPeriod (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает последний элемент среди потомков указанного элемента на указанном уровне.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ClosingPeriod( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 Эта функция прежде всего предназначена для использования в измерении времени, но может быть использована и для других измерений.  
  
-   Если выражение уровня указано, **ClosingPeriod** функция использует измерение, содержащее заданный уровень и возвращает последнего родственника из потомков элемента по умолчанию на заданном уровне.  
  
-   Если указано выражение уровня и выражение элемента, **ClosingPeriod** функция возвращает последнего родственника из потомков заданного элемента на заданном уровне.  
  
-   Если ни выражение уровня, ни выражение элемента указано, **ClosingPeriod** функция использует уровень по умолчанию и элемент из измерения (если таковые имеются) в кубе типа Time.  
  
 **ClosingPeriod** функция эквивалентна следующей инструкции многомерных Выражений:  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`.  
  
> [!NOTE]  
>  [OpeningPeriod](../mdx/openingperiod-mdx.md) функция подобна **ClosingPeriod** за тем исключением, которое **OpeningPeriod** функция возвращает первый родственный вместо последним элементом.  
  
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
 [Справочник по функциям многомерных Выражений & #40; Многомерные Выражения & #41;](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40;многомерных Выражений&#41;](../mdx/lastsibling-mdx.md)  
  
  
