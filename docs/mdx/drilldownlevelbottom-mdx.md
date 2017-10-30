---
title: "DrilldownLevelBottom (многомерные Выражения) | Документы Microsoft"
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
- DRILLDOWNLEVELBOTTOM
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownLevelBottom function
ms.assetid: c00a6a02-e618-4713-805a-870e042f2d51
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9ff1ff6edc4bd145b29c1158c843ba8ae1642705
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Детализирует углублением самые нижние элементы набора на указанном уровне и одним уровнем ниже.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DrilldownLevelBottom(Set_Expression, Count [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Numeric_Expression*  
 Необязательно. Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *Include_Calc_Members*  
 Необязательно. Ключевое слово, которое добавляет вычисляемые элементы в результаты углубленной детализации.  
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, **DrilldownLevelBottom** функция сортирует в порядке возрастания, потомков каждого элемента в заданном наборе согласно заданному значению, вычисленному по набору элементов-потомков. Если числовое выражение не задано, эта функция сортирует в порядке возрастания дочерние элементы каждого элемента в указанном наборе согласно значениям ячеек, представленным набором дочерних элементов, в соответствии с определением в контексте запроса. Это поведение аналогично поведению функций многомерных выражений BottomCount и Tail, которые возвращают набор элементов в естественном порядке без какой-либо сортировки.  
  
 После сортировки **DrilldownLevelBottom** функция возвращает набор, содержащий родительские элементы и количество дочерних элементов, указанные в *число*, с наименьшим значением.  
  
 **DrilldownLevelBottom** функция подобна [DrilldownLevel](../mdx/drilldownlevel-mdx.md) функции, но вместо включения всех потомков каждого элемента на заданном уровне **DrilldownLevelBottom** функция возвращает самый нижний количество дочерних элементов.  
  
 Запрос свойства XMLA MdpropMdxDrillFunctions позволяет проверить уровень поддержки, обеспечиваемой сервером для функций детализации; в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) подробные сведения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются три нижних потомка уровня категории продуктов согласно мере по умолчанию. В примере куба Adventure Works три нижних потомка для Accessories являются Tires и Tubes, Pumps и Panniers. В Management Studio в окне запроса MDX можно перейти в раздел Продукты | Категории продуктов | Элементы | Все продукты | Аксессуары, чтобы просмотреть весь список. Вы можете увеличить аргумент счетчика, чтобы вернуть больше элементов.  
  
```  
SELECT DrilldownLevelBottom   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 В следующем примере демонстрируется использование **include_calc_members** флаг, который используется для включения вычисляемых элементов в уровне детализации углублением. Мера [Reseller Order Count] добавляется **DrilldownLevelBottom** инструкции, чтобы убедиться, что результаты сортируются по этой мере. Чтобы увидеть вычисляемый элемент, необходимо увеличить счетчик по крайней мере до 9.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELBOTTOM(  
  [Product].[Product Categories].children ,  
  9,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [DrilldownLevel &#40; Многомерные Выражения &#41;](../mdx/drilldownlevel-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

