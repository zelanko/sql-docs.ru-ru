---
title: И (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 30cb8be449c58e10da5c2e91ebec936b3547581d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63249880"
---
# <a name="and-mdx"></a>AND (многомерные выражения)


  Выполняет логическое умножение двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, возвращающее значение true, если оба аргумента имеют значение **true**; в противном случае **false**.  
  
## <a name="remarks"></a>Примечания  
 **AND** оператор рассматривает оба выражения как логические (значение 0, соответствует **false**; в противном случае **true**) прежде, чем оператор выполнит логическое умножение. В следующей таблице показано как **AND** оператор выполнит логическое умножение.  
  
|*Expression1*|*Expression2*|Возвращаемое значение|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**false**|  
|**false**|**true**|**false**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Пример  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for clothing sales where the GPM is between 20% and 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] <= .3 AND   
      [Measures].[Gross Profit Margin] >= .2,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT NON EMPTY  
    [Sales Territory].[Sales Territory Country].Members ON 0,  
    [Product].[Category].[Clothing] ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
