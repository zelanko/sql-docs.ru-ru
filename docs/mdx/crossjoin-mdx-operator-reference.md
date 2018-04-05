---
title: '* (Перекрестное соединение) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft'
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
- '*'
dev_langs:
- kbMDX
helpviewer_keywords:
- '* (crossjoin operator)'
- crossjoin operator (*)
ms.assetid: e00cb260-0189-4c4e-b3d2-088f4421337b
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e192e0eacd926cde2c6548392b1523cfc3d0af12
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - Справочник по операторам многомерных Выражений
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
