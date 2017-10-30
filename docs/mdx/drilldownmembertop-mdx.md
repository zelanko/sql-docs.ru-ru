---
title: "DrilldownMemberTop (многомерные Выражения) | Документы Microsoft"
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
- DRILLDOWNMEMBERTOP
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownMemberTop function
ms.assetid: b6575544-1fd3-4fa1-aa2e-272d307c7750
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: da7f8a1c315d9ff3eb60c69e88726b521a59d17d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="drilldownmembertop-mdx"></a>DrilldownMemberTop (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Детализирует углублением элементы указанного набора, присутствующие во втором указанном наборе, ограничивая результирующий набор заданным количеством элементов. Эта функция может также детализировать углублением набор кортежей с использованием первой иерархии кортежей или дополнительно указанной иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DrillDownMemberTop(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expression>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *Иерархия*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Рекурсивные*  
 Ключевое слово, которое обозначает рекурсивное сравнение наборов.  
  
 *Include_Calc_Members*  
 Ключевое слово, позволяющее включать вычисляемые элементы в результаты углубленной детализации.  
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, **DrilldownMemberTop** функция сортирует в порядке убывания потомки каждого элемента в первом наборе согласно значению числового выражения, вычисленного над набором дочерних элементов. Если числовое выражение не указано, функция сортирует в порядке убывания потомки каждого элемента в первом наборе согласно значениям ячеек, представленных набором элементов-потомков, как определено контекстом запроса. Это поведение аналогично функциям многомерных выражений TopCount и Head (MDX), которые возвращают набор элементов в естественном порядке без какой-либо сортировки.  
  
 После сортировки **DrilldownMemberTop** функция возвращает набор, содержащий родительские элементы и количество дочерних элементов, указанные в *Count,* с наибольшее значение и содержащихся в обоих наборах.  
  
 Если **РЕКУРСИВНЫЕ** указано, функция сортирует первый набор, как было описано выше, а затем рекурсивно сравнивает элементы первого набора, организованные в иерархию, со вторым набором*.* Функция возвращает число верхних потомков каждого элемента первого набора, присутствующих во втором наборе.  
  
 Первый набор может содержать кортежи вместо элементов. Углубленная детализация кортежей является расширением OLE DB и возвращает набор кортежей вместо набора элементов.  
  
 **DrilldownMemberTop** функция подобна [DrilldownMember](../mdx/drilldownmember-mdx.md) работать, но вместо включения всех потомков каждого элемента первого набора, которые также представлять во втором наборе, **DrilldownMemberTop** функция возвращает число верхних потомков для каждого элемента.  
  
 Запрос свойства XMLA MdpropMdxDrillFunctions позволяет проверить уровень поддержки, обеспечиваемой сервером для функций детализации; в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) подробные сведения.  
  
## <a name="example"></a>Пример  
 В следующем примере детализируется углублением категория одежды и возвращаются три подкатегории одежды с наибольшим числом заказов на поставку.  
  
```  
SELECT DrilldownMemberTop   ({[Product].[Product Categories].[All Products],        
[Product].[Product Categories].[Category].Bikes,        
[Product].[Product Categories].[Category].Clothing},     
{[Product].[Product Categories].[Category].Clothing},     
3,     
[Measures].[Reseller Order Quantity])     
ON 0     
FROM [Adventure Works]     
WHERE [Measures].[Reseller Order Quantity]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

