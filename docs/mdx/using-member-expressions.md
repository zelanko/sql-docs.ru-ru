---
title: "Выражения элементов | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- members [MDX], expressions
- expressions [MDX], members
ms.assetid: 63c7af49-8bea-47c5-9566-a961f77d2a3d
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 727eb8f83a87f965342fdcf81c75fa03fe7dea18
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="using-member-expressions"></a>Выражения элементов
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 Существует много функций многомерных выражений, которые возвращают элементы. Полный список см. в разделе [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Дополнительные сведения об именах и ключи элементов см. в разделе [работа с членами, кортежей и наборов &#40; Многомерные Выражения &#41; ](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Многомерные Выражения &#41;](../mdx/expressions-mdx.md)  
  
  
