---
title: "Определение свойств иерархии куба | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 858e5f95c4c382b46d85a9f0abcae728bae102c1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="define-cube-hierarchy-properties"></a>Определение свойств иерархии куба
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Свойства иерархии куба позволяют указать уникальные настройки многоуровневых иерархий в измерениях куба на основе того же измерения базы данных. В следующей таблице описаны свойства иерархии куба.  
  
|Свойство|Description|  
|--------------|-----------------|  
|**Включено**|Указывает, включена ли иерархия для измерения куба.|  
|**HierarchyID**|Содержит уникальный идентификатор (ID) иерархии.|  
|**OptimizedState**|Определяет уровень оптимизации, применяемый к иерархии. Это свойство может иметь следующие значения:<br /><br /> **FullyOptimized**:<br />                    Экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> **NotOptimized**:<br />                    Экземпляр не создает дополнительных индексов.|  
|**Visible**|Определяет видимость иерархии кубов. Значение по умолчанию — **True**.|  
  
## <a name="see-also"></a>См. также  
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
