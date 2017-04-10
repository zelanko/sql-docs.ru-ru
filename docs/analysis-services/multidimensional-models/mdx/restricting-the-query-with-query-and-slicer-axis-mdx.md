---
title: "Ограничение запроса с помощью осей запроса и среза (многомерные выражения) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "многомерные выражения [службы Analysis Services], оси"
  - "запросы [многомерные выражения], оси"
  - "оси [многомерные выражения]"
  - "многомерные выражения [службы Analysis Services], оси"
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Ограничение запроса с помощью осей запроса и среза (многомерные выражения)
  При формировании инструкции многомерных выражений SELECT приложение обычно изучает куб и разбивает набор иерархий на два следующих подмножества.  
  
-   **Ось запроса**— набор иерархий, из которых данные извлекаются для нескольких элементов. Дополнительные сведения об осях запроса см. в разделе [Определение содержимого оси запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md).  
  
-   **Ось среза**— набор иерархий, из которых данные извлекаются для одного элемента. Дополнительные сведения об осях среза см. в разделе [Определение содержимого оси среза (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-slicer-axis-mdx.md).  
  
 Поскольку оси запроса и среза можно построить из нескольких иерархий запрашиваемого куба, эти термины позволяют отличать иерархии, которые используются запрашиваемым кубом, от иерархий, созданных в кубе, возвращаемом многомерным запросом.  
  
 Пример использования осей запроса и среза см. в разделе [Оси запроса и среза. Простой пример (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/using-query-and-slicer-axes-in-a-simple-example-mdx.md).  
  
## См. также  
 [Работа с элементами, кортежами и наборами (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  