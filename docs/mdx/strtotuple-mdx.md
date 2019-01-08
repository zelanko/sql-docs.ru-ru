---
title: StrToTuple (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 054786440afaf2b7ab458b4704bd5f8e2e26c135
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52524527"
---
# <a name="strtotuple-mdx"></a>StrToTuple (многомерные выражения)


  Возвращает кортеж, заданный строкой в формате Многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Specification*  
 Допустимое строковое выражение, явно или неявно задающее кортеж.  
  
## <a name="remarks"></a>Примечания  
 **StrToTuple** функция возвращает указанный набор. **StrToTuple** функция обычно используется вместе с определяемыми пользователем функциями для возвращения спецификации кортежа из внешней функции обратно в инструкцию многомерных Выражений.  
  
-   Когда используется флаг CONSTRAINED, спецификация кортежа должна содержать полное или неполное имя элемента. Этот флаг используется для уменьшения риска атак, использующих вставку инструкций SQL в указанную строку. Если указана строка, которую невозможно напрямую разрешить до полного или неполного имени элемента, то появится следующее сообщение об ошибке: «Нарушены ограничения, установленные флагом CONSTRAINED функции STRTOTUPLE».  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
