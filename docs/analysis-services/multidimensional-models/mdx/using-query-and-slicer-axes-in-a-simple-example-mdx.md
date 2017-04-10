---
title: "Оси запроса и среза. Простой пример (многомерные выражения) | Microsoft Docs"
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
  - "ось среза"
  - "ось запроса [многомерные выражения]"
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Оси запроса и среза. Простой пример (многомерные выражения)
  Пример в этом разделе демонстрирует простейший метод указания и использования осей запроса и среза.  
  
## Куб  
 Куб TestCube имеет два измерения: Route и Time. Каждому из них соответствует только одна пользовательская иерархия (Route и Time соответственно). Поскольку меры куба относятся к измерению Measures, куб имеет всего три измерения.  
  
## Запрос  
 Запрос должен возвращать матрицу, в которой меру «Пакеты» можно сравнивать по маршрутам и времени.  
  
 В следующем примере запроса многомерных выражений иерархии Route и Time являются осями запроса, а измерение Measures — осью среза. Функция [Members](../../../mdx/members-set-mdx.md) указывает, что в многомерном запросе для формирования набора будут использоваться элементы иерархии или уровня. Благодаря функции **Members** в многомерном запросе не нужно явно указывать каждый элемент каждой конкретной иерархии или уровня.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## Результаты  
 Запрос возвращает таблицу значений меры Packages для каждого пересечения осей измерений COLUMNS и ROWS. Таблица должна выглядеть следующим образом.  
  
||по воздуху|по морю|  
|-|---------|---------|  
|Первый квартал|60|50|  
|Второй квартал|45|45|  
  
## См. также  
 [Определение содержимого оси запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-query-axis-mdx.md)   
 [Определение содержимого оси среза (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/specifying-the-contents-of-a-slicer-axis-mdx.md)  
  
  