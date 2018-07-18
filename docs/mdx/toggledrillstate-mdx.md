---
title: ToggleDrillState (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a2ed3251b5bf8bc17e832f87947cfc41231d35c0
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743433"
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (многомерные выражения)


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
  
## <a name="remarks"></a>Примечания  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
