---
title: SetToStr (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57e74eb1c7db4aebdd01fde8fc48a425d7affa55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149285"
---
# <a name="settostr-mdx"></a>SetToStr (многомерные выражения)


  Возвращает строку в формате многомерных выражений, соответствующую указанному набору.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 Эта функция используется для передачи строкового представления набора внешней функции для дальнейшего анализа. Возвращаемая строка заключается в фигурные скобки {}, с каждым элементом в наборе разделяются запятыми.  
  
## <a name="example"></a>Пример  
 В следующем примере передается строка, состоящая из всех элементов иерархии атрибута Geography.Country.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
