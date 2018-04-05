---
title: И (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- AND
dev_langs:
- kbMDX
helpviewer_keywords:
- AND, MDX
ms.assetid: 398fd483-d010-4524-b115-0becad66f25c
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4ddc10c3c32b6ac2cd411e04afd1775bdd3fc02f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="and-mdx"></a>AND (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Логическое значение, которое возвращает значение true, если оба аргумента имеют значение **true**; в противном случае **false**.  
  
## <a name="remarks"></a>Remarks  
 **AND** оператор рассматривает оба выражения как логические значения (ноль, 0 — как **false**; в противном случае **true**), прежде чем оператор выполнит логическое умножение. В следующей таблице показано, как **AND** оператор выполнит логическое умножение.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
