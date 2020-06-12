---
title: Определение свойств измерения куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c58cf6a2f55e57c9faa65ddec72fe1bda6000c2
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547026"
---
# <a name="define-cube-dimension-properties"></a>Определение свойств измерения куба
  Измерение куба представляет собой экземпляр измерения базы данных в пределах куба. Измерение базы данных может быть использовано в нескольких кубах, а измерения нескольких кубов могут быть основаны на одном измерении базы данных. В следующей таблице описаны свойства измерения куба.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|Управляет тем, как агрегаты создаются конструктором статистических схем в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Это свойство может иметь следующие значения:<br /><br /> **Full**: каждый агрегат для куба должен включать элемент "Все".<br /><br /> **None**: ни один агрегат для куба не может включать элемент "Все". Это значение по умолчанию.<br /><br /> **Unrestricted**: на конструктор статистических схем не налагаются никакие ограничения.<br /><br /> **Default**: функциональное назначение такое же, как и у значения "Unrestricted".|  
|`Description`|Представляет описательное имя уровня.|  
|`DimensionID`|Содержит уникальный идентификатор (ID) измерения базы данных.|  
|`HierarchyUniqueNameStyle`|Определяет правила формирования уникальных имен для иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> `IncludeDimensionName`: имя измерения включается в качестве части имени иерархии. Это значение по умолчанию.<br /><br /> `ExcludeDimensionName`: имя измерения не включается в качестве части имени иерархии.|  
|`ID`|Содержит уникальный идентификатор измерения куба.|  
|`MemberUniqueNameStyle`|Определяет правила формирования уникальных имен для элементов иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> `Native`: службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически определяют уникальные имена элементов. Это значение по умолчанию.<br /><br /> `NamePath`: службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] формируют составное имя, содержащее имя каждого уровня и заголовок элемента.|  
|`Name`|Содержит понятное имя измерения куба. По умолчанию имя измерения куба является таким же, как и имя измерения базы данных, если только уже не определено измерение куба с таким же именем.|  
|`Visible`|Определяет, является ли измерение куба видимым. Значение по умолчанию — `True`.|  
  
## <a name="see-also"></a>См. также:  
 [Измерения (службы Analysis Services — многомерные данные)](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
