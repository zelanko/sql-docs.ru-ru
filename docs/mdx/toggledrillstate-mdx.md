---
title: ToggleDrillState (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58acac77e4826855997791476b0602699452b7b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63228083"
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
 (Необязательно.) Ключевое слово, которое обозначает рекурсивное сравнение наборов. **ToggleDrillState** функция представляет собой сочетание **DrillupMember** и **DrilldownMember** функции. Рекурсия действует, только если элемент находится в **DrilldownMember** состояния.  
  
 *Include_calc_members*  
 (Необязательно.) Флажок, указывающий, следует ли включать вычисленные элементы и должны ли они существовать на уровне детализации углублением.  
  
## <a name="remarks"></a>Примечания  
 **ToggleDrillState** функция переключает состояние детализации для каждого элемента второго набора, присутствующих в первом наборе. Первый набор может содержать кортежи любой размерности, однако второй набор должен содержать элементы одного измерения. **ToggleDrillState** функция представляет собой сочетание **DrillupMember** и **DrilldownMember** функции. Если член *m*из второго набора присутствует в первом наборе и этот элемент детализирован углублением (т. е. имеет потомка), затем `DrillupMember(Set_Expression1, {m})` применяется к кортежу первого набора или. Если это *m* свернут (т. е. не существует потомка элемента *m* , сразу после *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` применяется к первому набору.  
  
 Если необязательный **РЕКУРСИВНОГО** флаг используется, детализация углублением и обобщением применяются рекурсивно. Дополнительные сведения о флаге рекурсии см. в разделе [DrillupMember](../mdx/drillupmember-mdx.md) и [DrilldownMember](../mdx/drilldownmember-mdx.md) функции.  
  
 Запрос свойства XMLA MdpropMdxDrillFunctions позволяет проверить уровень поддержки, предоставляемой сервером для функций детализации; см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) сведения.  
  
 См. в разделе [журнал базы данных: Набор функций многомерных Выражений: Функция ToggleDrillState(), где есть](https://go.microsoft.com/fwlink/?LinkId=517759) сценарии и примеры, включающие эту функцию.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
