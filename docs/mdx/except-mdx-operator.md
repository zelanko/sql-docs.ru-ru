---
title: '- (За исключением) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт'
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690873"
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
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
