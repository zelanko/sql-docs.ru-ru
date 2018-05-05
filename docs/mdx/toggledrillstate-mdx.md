---
title: ToggleDrillState (многомерные Выражения) | Документы Microsoft
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
- TOGGLEDRILLSTATE
dev_langs:
- kbMDX
helpviewer_keywords:
- ToggleDrillState function
ms.assetid: 26fa1a0d-3ed1-45dc-955d-0591d49e4db9
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 63b5fb01cac2fe886bce15ded807b8e655d98056
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Переключает состояние детализации элементов между режимами углубленной детализации и свертки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ToggleDrillState(Set_Expression1,Set_Expression2 [, [RECURSIVE] [,INCLUDE_CALC_MEMBERS] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Рекурсивные*  
 (Необязательно.) Ключевое слово, которое обозначает рекурсивное сравнение наборов. **ToggleDrillState** функция представляет собой сочетание **DrillupMember** и **DrilldownMember** функции. Рекурсия только тогда, когда элемент находится в **DrilldownMember** состояния.  
  
 *Include_calc_members*  
 (Необязательно.) Флажок, указывающий, следует ли включать вычисленные элементы и должны ли они существовать на уровне детализации углублением.  
  
## <a name="remarks"></a>Замечания  
 **ToggleDrillState** функция переключает состояние детализации каждого элемента второго набора, присутствующего в первом наборе. Первый набор может содержать кортежи любой размерности, однако второй набор должен содержать элементы одного измерения. **ToggleDrillState** функция представляет собой сочетание **DrillupMember** и **DrilldownMember** функции. Если член *m*, второго набора присутствует в первом наборе, и этот элемент детализирован углублением (т. е. имеет потомка), затем `DrillupMember(Set_Expression1, {m})` применяется к кортежу первого набора или. Если данный *m* свернут (т. е. нет потомка элемента *m* , который следует сразу за *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` применяется к первому набору.  
  
 Если необязательный **РЕКУРСИВНЫЕ** флаг используется, детализация углублением и обобщением применяются рекурсивно. Дополнительные сведения о флаге рекурсии см. в разделе [DrillupMember](../mdx/drillupmember-mdx.md) и [DrilldownMember](../mdx/drilldownmember-mdx.md) функции.  
  
 Запрос свойства XMLA MdpropMdxDrillFunctions позволяет проверить уровень поддержки, обеспечиваемой сервером для функций детализации; в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) подробные сведения.  
  
 В разделе [журнала базы данных: задать функции многомерных Выражений: функция ToggleDrillState(), где есть](http://go.microsoft.com/fwlink/?LinkId=517759) сценарии и примеры, включающие эту функцию.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется детализация углублением элемента Australia в первом наборе и детализация обобщением элемента United States в первом наборе.  
  
```  
SELECT ToggleDrillState  
   ({[Geography].[Geography].[Country].Members, [Geography].[Geography].[Country].&[United States].Children},  
      {[Geography].[Geography].[Country].[Australia]  
      , [Geography].[Geography].[Country].&[United States]}  
      --, recursive  
      --, include_calc_members  
   ) ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
