---
title: ', перечислены ниже. (Диапазон) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 882082d503bf88f21566ac79ea4393a24ee551e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277902"
---
# <a name="-range-mdx"></a>, перечислены ниже. (Диапазон) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ)


  Выполняет операцию над наборами, которая возвращает естественно упорядоченный набор с двумя заданными элементами в качестве конечных точек, а также все элементы между этими двумя точками, включенные в виде элементов набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Параметры  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, содержащий заданные элементы и все элементы между ними.  
  
## <a name="remarks"></a>Примечания  
 Оба параметра должны указывать элементы одного уровня и иерархии данного измерения. Если оба параметра указывают один и тот же элемент **: (Диапазон)**  оператор возвращает набор, содержащий только указанный элемент. Если первый параметр равен Null, то набор содержит все элементы от начала уровня элемента, заданного во втором параметре, до этого элемента включительно. Если второй параметр равен Null, то набор содержит все элементы от элемента, заданного в первом параметре, до последнего элемента на том же уровне включительно.  
  
 Для этого оператора набора нет функционального эквивалента в языке многомерных выражений.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
