---
title: "- (За исключением) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft"
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
- '-'
dev_langs:
- kbMDX
helpviewer_keywords:
- Except operator [MDX]
- '- (except operator)'
ms.assetid: 8971a09d-b254-4c4c-a099-103664783589
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d06de38c64dda440d04d49c498653bcb52f8c6fa
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="except-mdx-operator"></a>За исключением оператора (многомерные Выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выполняет операцию над наборами, которая возвращает разность двух наборов, удаляя дубликаты элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression - Set_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, состоящий из элементов, не входящих одновременно в оба набора-аргумента.  
  
## <a name="remarks"></a>Замечания  
 **- (Разность множеств)** оператор функционально эквивалентен [за исключением](../mdx/except-mdx-function.md) функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование этого оператора:  
  
```  
// This query shows the quantity of orders for all product categories  
// with the exception of Components.  
SELECT   
   [Measures].[Order Quantity] ON COLUMNS,  
   [Product].[Product Categories].[All].Children   
   - [Product].[Product Categories].[Components] ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

