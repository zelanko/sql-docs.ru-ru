---
title: '- (За исключением) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft'
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
ms.openlocfilehash: cd788f04edad46e27c69ba3b5932cd2ffff35767
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="except-mdx-operator"></a>За исключением оператора (многомерные Выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
