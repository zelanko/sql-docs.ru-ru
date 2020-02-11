---
title: StrToTuple (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 232d1e94892165430867ec5217f8c87ccd625b48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036711"
---
# <a name="strtotuple-mdx"></a>StrToTuple (многомерные выражения)


  Возвращает кортеж, заданный в формате строки МНОГОМЕРных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Specification*  
 Допустимое строковое выражение, явно или неявно задающее кортеж.  
  
## <a name="remarks"></a>Remarks  
 Функция **StrToTuple** Возвращает указанный набор. Функция **StrToTuple** обычно используется с определяемыми пользователем функциями для возвращения спецификации кортежа из внешней функции обратно в ИНСТРУКЦИю многомерных выражений.  
  
-   Когда используется флаг CONSTRAINED, спецификация кортежа должна содержать полное или неполное имя элемента. Этот флаг используется для уменьшения риска атак, использующих вставку инструкций SQL в указанную строку. Если указана строка, которая не разрешается напрямую в полные или неполные имена элементов, возникает следующая ошибка: "нарушены ограничения, установленные флагом CONSTRAINED в функции STRTOTUPLE".  
  
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
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
