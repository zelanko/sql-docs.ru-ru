---
title: Тип данных CubeAttribute (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CubeAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b1df72c234fe7835d739e2b1835b01041aa9cbe6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319354"
---
# <a name="cubeattribute-data-type-assl"></a>Тип данных CubeAttribute (ASSL)
  Определяет тип-примитив, представляющий атрибут, связанный с [куба](../objects/cube-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[AggregationUsage](../properties/aggregationusage-element-assl.md), [заметки](../collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [ AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeID](../properties/id-element-assl.md)|  
|Производные элементы|[Атрибут](../objects/attribute-element-assl.md) ([атрибуты](../collections/attributes-element-assl.md) коллекцию [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Элемент *AttributeHierarchyOptimizedState* не поддерживается при запуске службы со значениями 1 или 2 свойства конфигурации DeploymentMode (режимы SharePoint или табличный, используемые для запуска баз данных PowerPivot и баз данных табличной модели).  
  
 Нельзя добавить атрибут как уровень иерархии, если свойство *AtttributeHierarchyEnabled*имеет значение FALSE и экземпляр работает в режиме DeploymentMode 1 или 2 (режим сервера SharePoint или табличный).  
  
 Атрибуты в [CubeDimension](dimension-data-type-assl.md) элемент, который не включен явно в [атрибуты](../collections/attributes-element-assl.md) коллекции становятся частью коллекции присвоенные им значения по умолчанию. После добавления в коллекцию атрибутов, атрибуты могут возвращаться [Discover](../../xmla/xml-elements-methods-discover.md) метод.  
  
 [AggregationUsage](../properties/aggregationusage-element-assl.md) управляет как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] автоматически статистических схем для атрибута. Элемент `AggregationUsage` не ограничивает любые статистические обработки, созданные для куба вручную.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
