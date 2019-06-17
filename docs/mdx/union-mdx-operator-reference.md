---
title: + (Объединение) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: be12a1af53957ab0d8f3347a0464dd987152bca0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63129823"
---
# <a name="union---mdx-operator-reference"></a>UNION - Справочник по операторам многомерных Выражений


  Выполняет операцию над наборами, которая возвращает объединение двух наборов с удалением повторяющихся элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Параметры  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, содержащий элементы обоих заданных наборов.  
  
## <a name="remarks"></a>Примечания  
 **+ (Объединение множеств)** оператор функционально эквивалентен [объединения &#40;многомерных Выражений&#41; ](../mdx/union-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
