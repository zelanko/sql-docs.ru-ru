---
title: "Унарные операторы | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- unary operators
ms.assetid: bf1b5518-6040-4484-9ce8-79c0eb4373a9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5b5aea52fb028a9c1d5345e60d4bfa400ecaa735
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="unary-operators"></a>Унарные операторы
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В языке многомерных выражений унарные операторы выполняют действия над одним операндом, к примеру, возвращая отрицательное или положительное значение числового выражения.  
  
 В языке многомерных выражений поддерживаются унарные операторы, перечисленные в следующей таблице.  
  
|Оператор|Description|  
|--------------|-----------------|  
|[-(Отрицательное значение)](../mdx/negative-mdx.md)|Возвращает отрицательное значение числового выражения.|  
|[+ (Положительное значение)](../mdx/positive-mdx.md)|Возвращает положительное значение числового выражения.|  
  
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
  
 Кроме того, используемые специальные унарные операторы для определения статистической операции, выполняемой по [RollupChildren](../mdx/rollupchildren-mdx.md) функции. Дополнительные сведения о специальных унарных операторах см. в разделе [Добавление нестандартного статистического выражения к измерению](../analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension.md).  
  
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Синтаксис многомерных Выражений &#41;](../mdx/operators-mdx-syntax.md)  
  
  

