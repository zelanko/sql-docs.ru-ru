---
title: "Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения) | Microsoft Docs"
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
  - "свойство ячейки FORE_COLOR"
  - "цвет фона [многомерные выражения]"
  - "ячейки [многомерные выражения]"
  - "цвета [многомерные выражения]"
  - "хранение сведений о цветах ячеек"
  - "цвет фона ячеек"
  - "свойство ячейки BACK_COLOR"
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)
  Свойства ячеек **FORE_COLOR** и **BACK_COLOR** хранят сведения о цвете соответственно текста и фона ячеек в формате операционной системы Microsoft Windows RGB (красный-зеленый-синий).  
  
 Допустимый диапазон обычных RGB-цветов: от нуля (0) до 16777215 (&H00FFFFFF). Старший байт числа в этом диапазоне всегда равен 0, следующие 3 байта (в порядке старшинства) определяют интенсивность красного, зеленого и синего компонентов соответственно. Интенсивность красного, зеленого и синего компонентов выражается числом от 0 до 255 (&HFF).  
  
## См. также  
 [Использование свойств ячеек (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/using-cell-properties-mdx.md)  
  
  