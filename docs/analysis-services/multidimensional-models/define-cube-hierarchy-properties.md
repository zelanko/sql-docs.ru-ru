---
title: "Определение свойств иерархии куба | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
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
ms.openlocfilehash: 13934070e4121913b82a2604acf26581cf27796f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="define-cube-hierarchy-properties"></a>Определение свойств иерархии куба
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Свойства иерархии куба позволяют указать уникальные настройки многоуровневых иерархий в измерениях куба на основе того же измерения базы данных. В следующей таблице описаны свойства иерархии куба.  
  
|Свойство|Description|  
|--------------|-----------------|  
|**Enabled**|Указывает, включена ли иерархия для измерения куба.|  
|**HierarchyID**|Содержит уникальный идентификатор (ID) иерархии.|  
|**OptimizedState**|Определяет уровень оптимизации, применяемый к иерархии. Это свойство может иметь следующие значения:<br /><br /> **FullyOptimized**:<br />                    Экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> **NotOptimized**:<br />                    Экземпляр не создает дополнительных индексов.|  
|**Visible**|Определяет видимость иерархии кубов. Значение по умолчанию — **True**.|  
  
## <a name="see-also"></a>См. также:  
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
