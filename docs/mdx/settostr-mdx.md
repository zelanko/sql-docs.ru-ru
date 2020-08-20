---
description: SetToStr (многомерные выражения)
title: SetToStr (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0317de06f3d68388fac5be752d26e27f0d373a89
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500447"
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
  
## <a name="remarks"></a>Remarks  
 Эта функция используется для передачи строкового представления набора внешней функции для дальнейшего анализа. Возвращаемая строка заключается в фигурные скобки {} , при этом каждый элемент в наборе отделяется запятыми.  
  
## <a name="example"></a>Пример  
 В следующем примере передается строка, состоящая из всех элементов иерархии атрибута Geography.Country.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
