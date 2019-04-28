---
title: Tail (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4563ec53f3ed12081e91b5010ae00a71b6c2feb3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62677340"
---
# <a name="tail-mdx"></a>Tail (многомерные выражения)


  Возвращает подмножество из конца набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Tail(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
## <a name="remarks"></a>Примечания  
 **Заключительного** функция возвращает заданное количество кортежей из конца указанного набора. Порядок элементов сохраняется. Значение по умолчанию *число* -1. Если заданное количество кортежей меньше 1, то функция возвращает пустой набор. Если заданное число кортежей превышает количество кортежей в наборе, то функция возвращает исходный набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Заключительного** функция используется для возвращения только последних пяти наборов в результате после результат упорядочен в обратном порядке с помощью **порядок** функции.  
  
```  
SELECT Tail  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BASC  
      )  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
