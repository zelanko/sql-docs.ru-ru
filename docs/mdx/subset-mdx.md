---
title: Subset (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 07d813587dc530924becbb187a970f78022e5476
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136094"
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
  
 *Запуск*  
 Допустимое числовое выражение, указывающее позицию первого возвращаемого кортежа.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
## <a name="remarks"></a>Примечания  
 Из указанного набора **подмножества** функция возвращает набор, содержащий указанное число кортежей, начиная с указанной позиции. Индекс начинается с 0, то есть 0 соответствует первому кортежу в заданном наборе, 1 — второму и т. д.  
  
 Если *число* не указан, функция возвращает все кортежи из *запустить* до конца набора.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Подмножества** функция используется для возврата только первые пять наборов в результате после упорядочивания результата с помощью **порядок** функции.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
