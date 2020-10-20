---
description: DrilldownLevelTop (многомерные выражения)
title: DrilldownLevelTop (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: af0ecdd3e53df131793f4703e154f96c51efc4e1
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194006"
---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (многомерные выражения)


  Детализирует углублением самые верхние элементы набора на указанном уровне и одним уровнем ниже.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DrilldownLevelTop(<Set_Expression>, <Count> [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *Include_Calc_Members*  
 Ключевое слово для добавления вычисляемых элементов в результаты углубленной детализации.  
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, функция **DrilldownLevelTop** сортирует в убывающем порядке дочерние элементы каждого элемента в указанном наборе в соответствии со значением числового выражения, вычисленным по набору дочерних элементов. Если числовое выражение не указано, функция сортирует в порядке убывания потомки каждого элемента в заданном наборе согласно значениям ячеек, представленных набором элементов-потомков, как определено контекстом запроса.  
  
 После сортировки функция **DrilldownLevelTop** возвращает набор, содержащий родительские элементы и количество дочерних элементов, указанное в параметре *Count,* с наибольшим значением.  
  
 Функция **DrilldownLevelTop** похожа на функцию [DrilldownLevel](../mdx/drilldownlevel-mdx.md) , но вместо включения всех дочерних элементов для каждого элемента на указанном уровне функция **DrilldownLevelTop** Возвращает самое верхнее количество дочерних элементов.  
  
 Запрос свойства XMLA Мдпропмдксдриллфунктионс позволяет проверить уровень поддержки, предоставляемый сервером для функций сверления; Дополнительные сведения см. в разделе [Поддерживаемые свойства xmla &#40;&#41;XMLA ](/analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются три верхних потомка уровня категории продуктов согласно мере по умолчанию. В примере куба Adventure Works три верхних потомка для Accessories являются Bike Racks, Bike Stands и Bottles and Cages. В Management Studio в окне запроса MDX можно перейти в раздел Продукты | Категории продуктов | Элементы | Все продукты | Аксессуары, чтобы просмотреть весь список. Вы можете увеличить аргумент счетчика, чтобы вернуть больше элементов.  
  
```  
SELECT DrilldownLevelTop   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 В следующем примере показано использование флага **include_calc_members** , который используется для включения вычисляемых элементов в уровень детализации. Мера [число заказов торгового посредника] включается в инструкцию **DrilldownLevelTop** , чтобы гарантировать сортировку возвращаемых значений по этой мере.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELTOP(  
  [Product].[Product Categories].children ,  
  2,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [DrilldownLevel &#40;&#41;многомерных выражений ](../mdx/drilldownlevel-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
