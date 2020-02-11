---
title: Определение свойств иерархии куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ace708cc4ee09295380b814bbf21f5a1c350974
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075709"
---
# <a name="define-cube-hierarchy-properties"></a>Определение свойств иерархии куба
  Свойства иерархии куба позволяют указывать уникальные настройки многоуровневых иерархий в измерениях куба на основе одного измерения базы данных. В следующей таблице описаны свойства иерархии куба.  
  
|Свойство|Description|  
|--------------|-----------------|  
|`Enabled`|Указывает, включена ли иерархия для измерения куба.|  
|`HierarchyID`|Содержит уникальный идентификатор (ID) иерархии.|  
|`OptimizedState`|Определяет уровень оптимизации, применяемый к иерархии. Это свойство может иметь следующие значения:<br /><br /> 
  `FullyOptimized`: экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> 
  `NotOptimized`: экземпляр не создает дополнительные индексы.|  
|`Visible`|Определяет видимость иерархии кубов. По умолчанию используется значение `True`.|  
  
## <a name="see-also"></a>См. также:  
 [Пользовательские иерархии](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
