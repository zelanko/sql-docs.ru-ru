---
title: ': (Диапазон) (многомерные выражения) | Документация Майкрософт'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6afc3a73b958062bd6472153b2452bc0e3fa6cfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020618"
---
# <a name="-range-mdx"></a>: (Диапазон) (многомерные выражения)


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
  
## <a name="remarks"></a>Remarks  
 Оба параметра должны указывать элементы одного уровня и иерархии данного измерения. Если оба параметра указывают один и тот же элемент, оператор **: (Range)** возвращает набор, содержащий только указанный элемент. Если первый параметр равен Null, то набор содержит все элементы от начала уровня элемента, заданного во втором параметре, до этого элемента включительно. Если второй параметр равен Null, то набор содержит все элементы от элемента, заданного в первом параметре, до последнего элемента на том же уровне включительно.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)  
  
  
