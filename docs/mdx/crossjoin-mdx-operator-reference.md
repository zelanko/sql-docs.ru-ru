---
title: '* (Перекрестное соединение) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 132b237fd8baa9c50dc254b02d90ed95d7159a0c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740603"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - Справочник по операторам многомерных Выражений


  Выполняет операцию над наборами, возвращающую перекрестное произведение двух наборов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>Параметр  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, содержащий перекрестное произведение обоих заданных наборов.  
  
## <a name="remarks"></a>Примечания  
 **\* (Перекрестное соединение)** оператор функционально эквивалентен [Crossjoin](../mdx/crossjoin-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This query returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
