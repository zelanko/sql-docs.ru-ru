---
description: Item (кортеж) (многомерные выражения)
title: Item (кортеж) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1e98e6901c018a6c8be5187024e5462cc8d19547
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483957"
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
  
 *String_Expression1*  
 Допустимое строковое выражение, обычно являющееся кортежем в форме строки.  
  
 *String_Expression2*  
 Допустимое строковое выражение, обычно являющееся кортежем в форме строки.  
  
 *Index*  
 Допустимое числовое выражение, указывающее кортеж по его позиции в возвращаемом наборе.  
  
## <a name="remarks"></a>Комментарии  
 Функция **Item** возвращает кортеж из указанного набора. Существует три возможных способа вызова функции **Item** :  
  
-   Если указано одно строковое выражение, функция **Item** Возвращает указанный кортеж. Пример: "([2005].Q3, [Store05])".  
  
-   Если указано более одного строкового выражения, функция **Item** возвращает кортеж, определенный указанными координатами. Количество строк должно совпадать с количеством осей, а каждая строка — обозначать уникальную иерархию. Пример: "[2005].Q3", "[Store05]".  
  
-   Если указано целое число, функция **Item** возвращает кортеж, который находится в позиции с отсчетом от нуля, указанной в параметре *index*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает ([1996],Sales):  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 В следующем примере используется выражение уровня и возвращается Internet Sales Amount для каждой административно-территориальной единицы (State-Province) Австралии (Australia), возвращается также процентное соотношение относительно общего значения Internet Sales Amount в Австралии (Australia). В этом примере используется функция Item для извлечения первого (и только кортежа) из набора, возвращенного функцией- **предками** .  
  
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
  
  
