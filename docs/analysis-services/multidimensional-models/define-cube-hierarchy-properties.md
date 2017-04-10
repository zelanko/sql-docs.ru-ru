---
title: "Определение свойств иерархии куба | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "иерархии [службы Analysis Services], многоуровневые"
  - "иерархии [службы Analysis Services], кубы"
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# Определение свойств иерархии куба
  Свойства иерархии куба позволяют указывать уникальные настройки многоуровневых иерархий в измерениях куба на основе одного измерения базы данных. В следующей таблице описаны свойства иерархии куба.  
  
|Свойство|Description|  
|--------------|-----------------|  
|**Включено**|Указывает, включена ли иерархия для измерения куба.|  
|**HierarchyID**|Содержит уникальный идентификатор (ID) иерархии.|  
|**OptimizedState**|Определяет уровень оптимизации, применяемый к иерархии. Это свойство может иметь следующие значения:<br /><br /> **FullyOptimized**:<br />                    Экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> **NotOptimized**:<br />                    Экземпляр не создает дополнительных индексов.|  
|**Visible**|Определяет видимость иерархии кубов. Значение по умолчанию — **True**.|  
  
## См. также  
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  