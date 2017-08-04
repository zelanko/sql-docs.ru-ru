---
title: "DrilldownLevelTop (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DRILLDOWNLEVELTOP
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownLevelTop function
ms.assetid: b3b45dd6-2ade-4dd7-83dd-849231e2e517
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d094ec3e2897bef5dfed1d98eddf82e115d84df5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, **DrilldownLevelTop** функция сортирует в порядке убывания потомки каждого элемента в заданном наборе согласно значению числового выражения, вычисленного над набором дочерних элементов. Если числовое выражение не указано, функция сортирует в порядке убывания потомки каждого элемента в заданном наборе согласно значениям ячеек, представленных набором элементов-потомков, как определено контекстом запроса.  
  
 После сортировки **DrilldownLevelTop** функция возвращает набор, содержащий родительские элементы и количество дочерних элементов, указанные в *Count,* с наибольшим значением.  
  
 **DrilldownLevelTop** функция подобна [DrilldownLevel](../mdx/drilldownlevel-mdx.md) функции, но вместо включения всех потомков каждого элемента на заданном уровне **DrilldownLevelTop** функция возвращает заданное количество дочерних элементов.  
  
 Запрос свойства XMLA MdpropMdxDrillFunctions позволяет проверить уровень поддержки, обеспечиваемой сервером для функций детализации; в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) подробные сведения.  
  
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
  
 В следующем примере демонстрируется использование **include_calc_members** флаг, который используется для включения вычисляемых элементов в уровне детализации углублением. Мера [Reseller Order Count] включается в **DrilldownLevelTop** инструкции, чтобы убедиться, что возвращаемые значения сортируются по этой мере.  
  
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
 [DrilldownLevel &#40; Многомерные Выражения &#41;](../mdx/drilldownlevel-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

