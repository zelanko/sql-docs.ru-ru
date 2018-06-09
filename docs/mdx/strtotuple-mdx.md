---
title: StrToTuple (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 35cd9cf849ce35bf82c839f0bbeeb657a75e990c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743233"
---
# <a name="strtotuple-mdx"></a>StrToTuple (многомерные выражения)


  Возвращает кортеж, заданный форматированной строкой многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Specification*  
 Допустимое строковое выражение, явно или неявно задающее кортеж.  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
