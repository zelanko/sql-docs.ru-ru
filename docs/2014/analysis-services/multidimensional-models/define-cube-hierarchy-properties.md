---
title: Определение свойств иерархии куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9ebe3b4a45791a9e5a9e136fed4e228666c8e49e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289821"
---
# <a name="define-cube-hierarchy-properties"></a>Определение свойств иерархии куба
  Свойства иерархии куба позволяют указывать уникальные настройки многоуровневых иерархий в измерениях куба на основе одного измерения базы данных. В следующей таблице описаны свойства иерархии куба.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`Enabled`|Указывает, включена ли иерархия для измерения куба.|  
|`HierarchyID`|Содержит уникальный идентификатор (ID) иерархии.|  
|`OptimizedState`|Определяет уровень оптимизации, применяемый к иерархии. Это свойство может иметь следующие значения:<br /><br /> `FullyOptimized`: Экземпляр создает индексы иерархии для улучшения производительности запросов. Это значение по умолчанию.<br /><br /> `NotOptimized`: Экземпляр не создает дополнительных индексов.|  
|`Visible`|Определяет видимость иерархии кубов. Значение по умолчанию — `True`.|  
  
## <a name="see-also"></a>См. также  
 [Пользовательские иерархии](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
