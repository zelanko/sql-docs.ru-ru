---
title: Унарные операторы | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9ec9ac3eef28c4deae08d577487599575852c132
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893552"
---
# <a name="unary-operators"></a>Унарные операторы


  В языке многомерных выражений унарные операторы выполняют действия над одним операндом, к примеру, возвращая отрицательное или положительное значение числового выражения.  
  
 В языке многомерных выражений поддерживаются унарные операторы, перечисленные в следующей таблице.  
  
|Operator|Описание|  
|--------------|-----------------|  
|[- (отрицательное значение)](../mdx/negative-mdx.md)|Возвращает отрицательное значение числового выражения.|  
|[+ (положительное значение)](../mdx/positive-mdx.md)|Возвращает положительное значение числового выражения.|  
  
 В следующем примере показано использование унарного оператора, возвращающего отрицательное значение меры.  
  
```  
WITH   
   MEMBER [Measures].[NegDiscountAmount] AS  
   -[Measures].[Discount Amount]  
SELECT   
   {[Measures].[Discount Amount],[Measures].[NegDiscountAmount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 Кроме того, многомерные выражения используют специальные унарные операторы для определения статистической операции, выполняемой функцией [RollupChildren](../mdx/rollupchildren-mdx.md) . Дополнительные сведения об этих специальных унарных операторах см. в разделе [Добавление настраиваемого статистического выражения в измерение](https://docs.microsoft.com/analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension).  
  
## <a name="see-also"></a>См. также  
 [Синтаксис &#40;операторов многомерных выражений&#41;](../mdx/operators-mdx-syntax.md)  
  
  
