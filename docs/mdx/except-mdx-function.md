---
title: EXCEPT (многомерные Выражения) | Документы Microsoft
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
- EXCEPT
dev_langs:
- kbMDX
helpviewer_keywords:
- Except function
ms.assetid: 5d832c82-1e6d-4308-9c26-7edb8afe11dd
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 061b4226e0fe884f04d203e2fca575fe7b4574b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="except-mdx-function"></a>EXCEPT, функция (многомерные Выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Замечания  
 Если **все** будет указано, функция сохраняет повторяющиеся значения, обнаруженные в первом наборе; повторяющиеся значения из второго набора удаляются. Функция возвращает элементы в порядке их следования в первом наборе.  
  
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
  
## <a name="see-also"></a>См. также  
 [- &#40;За исключением&#41; &#40;многомерных Выражений&#41;](../mdx/except-mdx-operator.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
