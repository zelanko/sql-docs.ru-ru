---
title: '- (За исключением) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 618beda530627898cdf55f08be5071fd7568688c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740703"
---
# <a name="except-mdx-operator"></a>За исключением оператора (многомерные Выражения)


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
  
## <a name="remarks"></a>Примечания  
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
  
  
