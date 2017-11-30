---
title: ": (Диапазон) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ':'
dev_langs: kbMDX
helpviewer_keywords:
- ': (range operator)'
- range operator (:)
ms.assetid: f9b36aca-4efd-49b4-9e4f-12914c1b24a6
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 698269bd47d9fb7fee4617246edeebc98bac5bb3
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="-range-mdx"></a>: (Диапазон) (многомерные Выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет операцию над наборами, которая возвращает естественно упорядоченный набор с двумя заданными элементами в качестве конечных точек, а также все элементы между этими двумя точками, включенные в виде элементов набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Параметры  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, содержащий заданные элементы и все элементы между ними.  
  
## <a name="remarks"></a>Замечания  
 Оба параметра должны указывать элементы одного уровня и иерархии данного измерения. Если оба параметра указывают один и тот же элемент **: (диапазон)** оператор возвращает набор, содержащий только указанный элемент. Если первый параметр равен Null, то набор содержит все элементы от начала уровня элемента, заданного во втором параметре, до этого элемента включительно. Если второй параметр равен Null, то набор содержит все элементы от элемента, заданного в первом параметре, до последнего элемента на том же уровне включительно.  
  
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
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
