---
title: "Определение свойств атрибутов куба | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
helpviewer_keywords: cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5c45283b8f78802445028b96ce40395189cd55f9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="define-cube-attribute-properties"></a>Определение свойств атрибутов куба
  Свойства атрибутов куба позволяют указать уникальные настройки для атрибутов измерений в кубе на основании того же измерения базы данных. В следующей таблице приводится описание свойств атрибутов куба.  
  
|Свойство|Description|  
|--------------|-----------------|  
|**AggregationUsage**|Определяет, каким образом мастер статистических схем будет создавать агрегаты для атрибута. Значение по умолчанию — **Default**. Это свойство может иметь следующие значения:<br /><br /> **Default**:<br />                    Мастер статистических схем применяет роль по умолчанию на основании типа атрибута (Full для ключей, Unrestricted для остальных).<br /><br /> **None**:<br />                    Ни один агрегат для куба не должен включать этот атрибут.<br /><br /> **Unrestricted**:<br />                    На мастер статистических схем не налагается никаких ограничений.<br /><br /> **Full**:<br />                    Каждый агрегат для куба должен включать этот атрибут.|  
|**AttributeHierarchyEnabled**|Указывает, включена ли иерархия атрибута в этом измерении куба. Это позволяет отключать иерархии атрибута в определенных кубах или ролях измерения. Эта установка не имеет действия, если отключена базовая иерархия атрибута. Значение по умолчанию — **True**.|  
|**OptimizedState**|Указывает, оптимизирована ли иерархия атрибутов в этом измерении куба. Это позволяет оптимизировать иерархии атрибута в определенных кубах или ролях измерения. Эта установка не имеет действия, если базовая иерархия атрибута не оптимизирована. Значение по умолчанию — **FullyOptimized**. Это свойство может иметь следующие значения:<br /><br /> **FullyOptimized**: экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> **NotOptimized**:<br />                    Экземпляр не создает дополнительных индексов.|  
|**AttributeHierarchyVisible**|Указывает, видима ли иерархия атрибута в этом измерении куба. Это позволяет иерархии атрибутов быть видимой в определенных кубах или ролях измерения. Эта установка не имеет действия, если основная иерархия атрибутов не видима. Значение по умолчанию — **True**.|  
|**AttributeID**|Содержит уникальный идентификатор атрибута.|  
  
## <a name="see-also"></a>См. также  
 [Определение свойств измерения куба](../../analysis-services/multidimensional-models/define-cube-dimension-properties.md)   
 [Определение свойств иерархии куба](../../analysis-services/multidimensional-models/define-cube-hierarchy-properties.md)  
  
  
