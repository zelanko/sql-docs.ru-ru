---
title: Ограничение запроса с помощью осей запроса и среза (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2a7d69055d3d60f8805a7cf7e8b9f1a98b9c01e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048186"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>Ограничение запроса с помощью осей запроса и среза (многомерные выражения)
  При формировании инструкции многомерных выражений SELECT приложение обычно изучает куб и разбивает набор иерархий на два следующих подмножества.  
  
-   **Ось запроса**— набор иерархий, из которых данные извлекаются для нескольких элементов. Дополнительные сведения об осях запроса см. в разделе [Определение содержимого оси запроса (многомерные выражения)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Ось среза**— набор иерархий, из которых данные извлекаются для одного элемента. Дополнительные сведения об осях среза см. в разделе [Определение содержимого оси среза (многомерные выражения)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Поскольку оси запроса и среза можно построить из нескольких иерархий запрашиваемого куба, эти термины позволяют отличать иерархии, которые используются запрашиваемым кубом, от иерархий, созданных в кубе, возвращаемом многомерным запросом.  
  
 Пример использования осей запроса и среза см. в разделе [Оси запроса и среза. Простой пример (многомерные выражения)](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами, кортежами и наборами &#40;многомерных Выражений&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
