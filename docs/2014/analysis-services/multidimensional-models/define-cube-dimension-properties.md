---
title: Определение свойств измерения куба | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bc40ef64b7b5e9b92d0e170d89ed388a90ff01c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188123"
---
# <a name="define-cube-dimension-properties"></a>Определение свойств измерения куба
  Измерение куба представляет собой экземпляр измерения базы данных в пределах куба. Измерение базы данных может быть использовано в нескольких кубах, а измерения нескольких кубов могут быть основаны на одном измерении базы данных. В следующей таблице описаны свойства измерения куба.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|Управляет созданием статистических схем конструктором статистических схем в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это свойство может иметь следующие значения:<br /><br /> **Full**: каждый агрегат для куба должен включать элемент "Все".<br /><br /> **None**: ни один агрегат для куба не может включать элемент "Все". Это значение по умолчанию.<br /><br /> **Unrestricted**: на конструктор статистических схем не налагаются никакие ограничения.<br /><br /> **Default**: функциональное назначение такое же, как и у значения "Unrestricted".|  
|`Description`|Представляет описательное имя уровня.|  
|`DimensionID`|Содержит уникальный идентификатор (ID) измерения базы данных.|  
|`HierarchyUniqueNameStyle`|Определяет правила формирования уникальных имен для иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> `IncludeDimensionName`: Имя измерения включается в качестве части имени иерархии. Это значение по умолчанию.<br /><br /> `ExcludeDimensionName`: Имя измерения не включается в качестве части имени иерархии.|  
|`ID`|Содержит уникальный идентификатор измерения куба.|  
|`MemberUniqueNameStyle`|Определяет правила формирования уникальных имен для элементов иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> `Native`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически определяют уникальные имена элементов. Это значение по умолчанию.<br /><br /> `NamePath`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] формирует составное имя, содержащее имя каждого уровня и заголовок элемента.|  
|`Name`|Содержит понятное имя измерения куба. По умолчанию имя измерения куба является таким же, как и имя измерения базы данных, если только уже не определено измерение куба с таким же именем.|  
|`Visible`|Определяет, является ли измерение куба видимым. Значение по умолчанию — `True`.|  
  
## <a name="see-also"></a>См. также  
 [Измерения &#40;службы Analysis Services — многомерные данные&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  