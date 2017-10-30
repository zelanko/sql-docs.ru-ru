---
title: "SetToStr (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SETTOSTR
dev_langs:
- kbMDX
helpviewer_keywords:
- SetToStr function
ms.assetid: b761e002-26cd-460e-b424-fb8e306746fa
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e0a2db653917d53ac25c290bd6dc14f3afe2cd09
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="settostr-mdx"></a>SetToStr (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку в формате многомерных выражений, соответствующую указанному набору.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Замечания  
 Эта функция используется для передачи строкового представления набора внешней функции для дальнейшего анализа. Возвращаемая строка заключается в фигурные скобки {}, элементы в наборе разделяются запятыми.  
  
## <a name="example"></a>Пример  
 В следующем примере передается строка, состоящая из всех элементов иерархии атрибута Geography.Country.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

