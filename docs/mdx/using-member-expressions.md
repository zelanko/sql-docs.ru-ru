---
title: Выражения элементов | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7abc83ae3483afedaa540c8fdcff0383af6ae994
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743774"
---
# <a name="using-member-expressions"></a>Выражения элементов


  Выражение элемента включает в себя идентификатор элемента, функцию элемента либо выражение, которое может быть преобразовано в элемент.  
  
 Идентификаторы элементов могут иметь много различных форматов. Самая простая форма идентификатора элемента состоит из имени элемента. Например:  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 Однако если существует несколько элементов с одним и тем же именем в различных иерархиях, нет способа определить, какой элемент будет возвращен запросом. Например, следующий запрос запрашивает данные для элемента с именем [CY 2004]. Запрос выполняется успешно, но в кубе Adventure Works существует по крайней мере шесть элементов с таким именем:  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 Поэтому наиболее надежная форма идентификатора элемента — уникальное имя элемента, которое гарантирует идентификацию элемента в кубе. Службы Analysis Services могут формировать уникальные имена несколькими способами, однако уникальное имя всегда состоит как минимум из двух идентификаторов: имени измерения и имени (или ключа) элемента. Уникальное имя имеет следующий формат.  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 Ниже приведены некоторые примеры уникальных имен элементов из куба Adventure Works:  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 Существует много функций многомерных выражений, которые возвращают элементы. Полный список см. в разделе [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Дополнительные сведения об именах и ключи элементов см. в разделе [работа с элементами, кортежами и наборами &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>См. также  
 [Выражения &#40;многомерных Выражений&#41;](../mdx/expressions-mdx.md)  
  
  
