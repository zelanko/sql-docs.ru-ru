---
title: Ограничение запроса с помощью запроса и ось среза (многомерные Выражения) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ad9f1b3a60707a0a10c9b15865286e1ad53eb2c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52508467"
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>Запрос многомерных выражений и ось среза — ограничение запроса
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  При формировании инструкции многомерных выражений SELECT приложение обычно изучает куб и разбивает набор иерархий на два следующих подмножества.  
  
-   **Ось запроса**— набор иерархий, из которых данные извлекаются для нескольких элементов. Дополнительные сведения об осях запроса см. в разделе [Определение содержимого оси запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Ось среза**— набор иерархий, из которых данные извлекаются для одного элемента. Дополнительные сведения об осях среза см. в разделе [Определение содержимого оси среза (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Поскольку оси запроса и среза можно построить из нескольких иерархий запрашиваемого куба, эти термины позволяют отличать иерархии, которые используются запрашиваемым кубом, от иерархий, созданных в кубе, возвращаемом многомерным запросом.  
  
 Пример использования осей запроса и среза см. в разделе [Оси запроса и среза. Простой пример (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами, кортежами и наборами (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
