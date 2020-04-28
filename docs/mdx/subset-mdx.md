---
title: Subset (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b1f9a79c0e0ba6d578b82d7b1d072f3543888a1c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036699"
---
# <a name="subset-mdx"></a>Subset (многомерные выражения)


  Возвращает подмножество кортежей указанного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Start*  
 Допустимое числовое выражение, указывающее позицию первого возвращаемого кортежа.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
## <a name="remarks"></a>Remarks  
 Из указанного набора функция **подмножества** возвращает подмножество, содержащее указанное число кортежей, начиная с указанной начальной позиции. Индекс начинается с 0, то есть 0 соответствует первому кортежу в заданном наборе, 1 — второму и т. д.  
  
 Если параметр *Count* не указан, функция возвращает все кортежи от *начала* до конца набора.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. Функция **подмножества** используется для возвращения только первых пяти наборов в результате, когда результат упорядочивается с помощью функции **Order** .  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
