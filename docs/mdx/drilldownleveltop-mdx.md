---
title: DrilldownLevelTop (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d6532998f65625bf3dacd11de2949a3478ba6ea
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146219"
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
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, **DrilldownLevelTop** функция сортирует в порядке убывания потомки каждого элемента в заданном наборе согласно значению числового выражения, вычисленного над набор дочерних элементы. Если числовое выражение не указано, функция сортирует в порядке убывания потомки каждого элемента в заданном наборе согласно значениям ячеек, представленных набором элементов-потомков, как определено контекстом запроса.  
  
 После сортировки **DrilldownLevelTop** функция возвращает набор, содержащий родительские элементы и столько дочерних элементов, указанные в *Count,* с наибольшим значением.  
  
 **DrilldownLevelTop** функция аналогична [DrilldownLevel](../mdx/drilldownlevel-mdx.md) функции, но вместо включения всех потомков каждого элемента на заданном уровне, **DrilldownLevelTop** функция возвращает число верхних потомков.  
  
 Запрос свойства XMLA MdpropMdxDrillFunctions позволяет проверить уровень поддержки, предоставляемой сервером для функций детализации; см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) сведения.  
  
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
  
 В следующем примере демонстрируется использование **include_calc_members** флаг, используемый для включения вычисляемых элементов в уровне детализации углублением. Мера [Reseller Order Count] включается в **DrilldownLevelTop** оператор, гарантирующий, что возвращаемые значения сортируются по этой мере.  
  
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
  
## <a name="see-also"></a>См. также  
 [DrilldownLevel (многомерные выражения)](../mdx/drilldownlevel-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
