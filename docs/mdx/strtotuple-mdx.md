---
title: "StrToTuple (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: STRTOTUPLE
dev_langs: kbMDX
helpviewer_keywords: StrToTuple function
ms.assetid: e162cc01-cddd-4654-baab-d73abdc33b80
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3c44c082ed36e8fb78f04788a2bd24d19e16bab5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="strtotuple-mdx"></a>StrToTuple (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает кортеж, заданный форматированной строкой многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Specification*  
 Допустимое строковое выражение, явно или неявно задающее кортеж.  
  
## <a name="remarks"></a>Замечания  
 **StrToTuple** функция возвращает указанный набор. **StrToTuple** функция обычно используется с пользовательскими функциями для возвращения спецификации кортежа из внешней функции обратно в инструкцию многомерных Выражений.  
  
-   Когда используется флаг CONSTRAINED, спецификация кортежа должна содержать полное или неполное имя элемента. Этот флаг используется для уменьшения риска атак, использующих вставку инструкций SQL в указанную строку. Если строка, которое не имена напрямую разрешаться в полное или неполное элементов, возникает следующая ошибка: «ограничения, установленные флагом CONSTRAINED функции STRTOTUPLE нарушены.»  
  
-   Когда флаг CONSTRAINED не используется, заданный кортеж может быть разрешен в допустимое многомерное выражение, возвращающее кортеж.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается мера Reseller Sales Amount для элемента Bayern для 2004 календарного года. Предоставленная спецификация кортежа содержит допустимое многомерное кортежное выражение.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается мера Reseller Sales Amount для элемента Bayern для 2004 календарного года. Предоставленная спецификация кортежа содержит полные названия элементов, требуемые для флага CONSTRAINED.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается мера Reseller Sales Amount для элемента Bayern для 2004 календарного года. Предоставленная спецификация кортежа содержит допустимое многомерное кортежное выражение.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается сообщение об ошибке, поскольку используется флаг CONSTRAINED. Хотя предоставленная спецификация кортежа содержит допустимое многомерное кортежное выражение, флаг CONSTRAINED требует полного или неполного имени элемента в спецификации кортежа.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
