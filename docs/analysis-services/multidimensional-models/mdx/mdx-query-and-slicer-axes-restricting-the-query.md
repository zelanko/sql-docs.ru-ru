---
title: Ограничение запроса с помощью запроса и оси среза (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c19bdf8b4850add274875fbe9af305d56a0aef4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>Многомерных Выражений оси запроса и среза - ограничение запроса
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  При формировании инструкции многомерных выражений SELECT приложение обычно изучает куб и разбивает набор иерархий на два следующих подмножества.  
  
-   **Ось запроса**— набор иерархий, из которых данные извлекаются для нескольких элементов. Дополнительные сведения об осях запроса см. в разделе [Определение содержимого оси запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Ось среза**— набор иерархий, из которых данные извлекаются для одного элемента. Дополнительные сведения об осях среза см. в разделе [Определение содержимого оси среза (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Поскольку оси запроса и среза можно построить из нескольких иерархий запрашиваемого куба, эти термины позволяют отличать иерархии, которые используются запрашиваемым кубом, от иерархий, созданных в кубе, возвращаемом многомерным запросом.  
  
 Пример использования осей запроса и среза см. в разделе [Оси запроса и среза. Простой пример (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>См. также:  
 [Работа с членами, кортежей и наборов & #40; Многомерные Выражения & #41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
