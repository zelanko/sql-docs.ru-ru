---
title: "Subset (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- subset
dev_langs:
- kbMDX
helpviewer_keywords:
- Subset function
ms.assetid: 49a7cd28-cd6f-4ae7-8c91-94a8652a97a5
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0496a6481cebf95e67a6f41a95ed37c522e44a13
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="subset-mdx"></a>Subset (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает подмножество кортежей указанного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Запуск*  
 Допустимое числовое выражение, указывающее позицию первого возвращаемого кортежа.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
## <a name="remarks"></a>Замечания  
 Из указанного набора **подмножества** функция возвращает подмножество, которое содержит заданное количество кортежей, начиная с указанной начальной позиции. Индекс начинается с 0, то есть 0 соответствует первому кортежу в заданном наборе, 1 — второму и т. д.  
  
 Если *число* не указан, функция возвращает все кортежи из *запустить* до конца набора.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Подмножества** функция используется для возвращения только первые пять наборов в результате после упорядочивания результата с помощью **порядок** функции.  
  
```  
SELECT Subset  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,0  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

