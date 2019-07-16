---
title: Item (кортеж) (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5740095752b482430cd718d0e2bff813449d92ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105225"
---
# <a name="item-tuple-mdx"></a>Item (кортеж) (многомерные выражения)


  Возвращает кортеж из набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Выражение String_Expression1*  
 Допустимое строковое выражение, обычно являющееся кортежем в форме строки.  
  
 *Выражение String_Expression2*  
 Допустимое строковое выражение, обычно являющееся кортежем в форме строки.  
  
 *Index*  
 Допустимое числовое выражение, указывающее кортеж по его позиции в возвращаемом наборе.  
  
## <a name="remarks"></a>Примечания  
 **Элемент** функция возвращает кортеж из указанного набора. Существует три возможных способа вызвать **элемент** функции:  
  
-   Если одно строковое выражение указано, **элемент** функция возвращает заданный кортеж. Пример: "([2005].Q3, [Store05])".  
  
-   Если указано более одного строкового выражения, **элемент** функция возвращает кортеж, определяемый по указанным координатам. Количество строк должно совпадать с количеством осей, а каждая строка — обозначать уникальную иерархию. Пример: "[2005].Q3", "[Store05]".  
  
-   Если указано целое число, **элемент** функция возвращает кортеж, который находится в позиции (с нуля), заданной параметром *индекс*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает ([1996],Sales):  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 В следующем примере используется выражение уровня и возвращается Internet Sales Amount для каждой административно-территориальной единицы (State-Province) Австралии (Australia), возвращается также процентное соотношение относительно общего значения Internet Sales Amount в Австралии (Australia). В этом примере используется функция Item для извлечения первый (и только кортежа) из набора, возвращаемого **предков** функции.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
