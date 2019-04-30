---
title: TupleToStr (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f07e71e5b8314320f76be4496744da5a9d9e81a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208461"
---
# <a name="tupletostr-mdx"></a>TupleToStr (многомерные выражения)


  Возвращает строку в формате Многомерных выражений, соответствующую указанному кортежу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
## <a name="remarks"></a>Примечания  
 Эта функция используется для передачи строкового представления кортежа внешней функции для дальнейшего анализа. Возвращаемая строка заключается в фигурные скобки {} и каждого элемента, если более чем один явным образом в кортеже, разделенные запятой.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает строку ([Date]. [ Calendar Year]. & [2001], [Geography]. [Geography]. [Страна]. & [United States]):  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 Следующий пример возвращает точно такую же строку, как и предыдущий пример.  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
