---
description: Except (многомерные выражения)
title: Except (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6e4cd8dcf3a8c3100a064e8ba5888060477de979
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341510"
---
# <a name="except-mdx-function"></a>Except (многомерные выражения)


  Обрабатывает два набора и удаляет кортежи из первого набора, существующие во втором наборе, сохраняя при необходимости одинаковые элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 Если указан параметр **ALL** , функция оставляет дубликаты, найденные в первом наборе; дубликаты, найденные во втором наборе, будут по-прежнему удалены. Функция возвращает элементы в порядке их следования в первом наборе.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование этой функции.  
  
```  
   //This query shows the quantity of orders for all products,  
   //with the exception of Components, which are not  
   //sold.  
SELECT   
   [Date].[Month of Year].Children  ON COLUMNS,  
   Except  
      ([Product].[Product Categories].[All].Children ,  
         {[Product].[Product Categories].[Components]}  
      ) ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   ([Measures].[Order Quantity])  
```  
  
## <a name="see-also"></a>См. также:  
 [-&#40;, кроме&#41; &#40;многомерных выражений&#41;](../mdx/except-mdx-operator.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
