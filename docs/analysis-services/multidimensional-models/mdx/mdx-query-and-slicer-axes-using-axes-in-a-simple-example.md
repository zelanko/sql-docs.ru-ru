---
title: "С помощью осей запроса и среза простой пример (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e27b8a961e692a9b1757573e4c735949fc537153
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-query-and-slicer-axes---using-axes-in-a-simple-example"></a>Многомерных Выражений оси запроса и среза - с помощью осей простой пример
  Пример в этом разделе демонстрирует простейший метод указания и использования осей запроса и среза.  
  
## <a name="the-cube"></a>Куб  
 Куб TestCube имеет два измерения: Route и Time. Каждому из них соответствует только одна пользовательская иерархия (Route и Time соответственно). Поскольку меры куба относятся к измерению Measures, куб имеет всего три измерения.  
  
## <a name="the-query"></a>Запрос  
 Запрос должен возвращать матрицу, в которой меру «Пакеты» можно сравнивать по маршрутам и времени.  
  
 В следующем примере запроса многомерных выражений иерархии Route и Time являются осями запроса, а измерение Measures — осью среза. Функция [Members](../../../mdx/members-set-mdx.md) указывает, что в многомерном запросе для формирования набора будут использоваться элементы иерархии или уровня. Благодаря функции **Members** в многомерном запросе не нужно явно указывать каждый элемент каждой конкретной иерархии или уровня.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>Результаты  
 Запрос возвращает таблицу значений меры Packages для каждого пересечения осей измерений COLUMNS и ROWS. Таблица должна выглядеть следующим образом.  
  
||по воздуху|по морю|  
|-|---------|---------|  
|Первый квартал|60|50|  
|Второй квартал|45|45|  
  
## <a name="see-also"></a>См. также  
 [Определение содержимого оси запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Определение содержимого оси среза (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
