---
title: "Extract (многомерные Выражения) | Документы Microsoft"
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
- EXTRACT
dev_langs:
- kbMDX
helpviewer_keywords:
- Extract function
ms.assetid: c0d27d31-e36e-4b7f-bb86-1e4707351392
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e18c7ac7dcf37ce41bc7917c9d7170a815c1f58
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="extract-mdx"></a>Extract (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор кортежей из извлеченных элементов иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Hierarchy_Expression1*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Hierarchy_Expression2*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Замечания  
 **Извлечь** функция возвращает набор, состоящий из кортежей из извлеченных элементов иерархии. Для каждого кортежа из указанного набора элементы из указанных иерархий извлекаются в новые кортежи результирующего набора. Эта функция всегда удаляет повторяющиеся кортежи.  
  
 **Извлечь** Функция противоположна из [Crossjoin](../mdx/crossjoin-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 Следующий запрос показывает использование **извлечь** для одного набора кортежей, возвращенных **NonEmpty** функции:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

