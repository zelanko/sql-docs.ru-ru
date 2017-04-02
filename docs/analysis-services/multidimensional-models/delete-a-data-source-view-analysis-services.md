---
title: "Удаление представления источников данных (службы Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
  - "удаление представлений источника данных"
  - "представления источников данных [службы Analysis Services], удаление"
  - "удаление представлений источников данных"
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Удаление представления источников данных (службы Analysis Services)
  При отсутствии необходимости использования файла представления источников данных (DSV) в проекте OLAP его можно удалить из проекта среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Удаление DSV необратимо. Восстановление удаленного источника DSV в проекте среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] невозможно.  
  
 Файлы представления источников данных (DSV), от которых зависят другие объекты, не могут быть удалены из базы данных среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , открытой в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме «в сети». Для удаления DSV из проекта, который имеет подключение к базе данных, запущенной на сервере, прежде всего необходимо удалить все объекты базы данных среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , зависящие от самого DSV.  
  
 Удаление DSV сделает недействительными все зависящие от него объекты среды [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , поэтому перед удалением DSV обратите внимание на список всех связанных с ним объектов. Внимательно изучите список объектов, убедитесь, что в нем отсутствуют объекты, необходимые для дальнейшего использования.  
  
 ![Диалоговое окно «Удаление объектов»](../../analysis-services/multidimensional-models/media/ssas-olapdsv-deleteobjects.gif "Диалоговое окно «Удаление объектов»")  
  
## См. также  
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Изменение свойств в представлении источника данных (службы Analysis Services)](../../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  