---
title: Тип данных CubeAttribute (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- CubeAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f29ee606b82d0f4ab7207d0fa4562fa0be1563b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cubeattribute-data-type-assl"></a>Тип данных CubeAttribute (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет примитивный тип данных, представляющий атрибут, связанный с элементом [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) .  
  
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
|Дочерние элементы|[AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md), [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md), [AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|  
|Производные элементы|Объект[Attribute](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md) объектов [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 *AttributeHierarchyOptimizedState* элемент не поддерживается при запуске службы со значениями свойства конфигурации DeploymentMode 1 или 2 (режим SharePoint или табличный, используемые для запуска [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и табличной модели базы данных).  
  
 Нельзя добавить атрибут как уровень иерархии, если свойство *AtttributeHierarchyEnabled*имеет значение FALSE и экземпляр работает в режиме DeploymentMode 1 или 2 (режим сервера SharePoint или табличный).  
  
 Атрибуты в элементе [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) , неявно включенные в коллекцию [Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md) , становятся частью коллекции и имеют присвоенные им значения по умолчанию. После добавления в коллекцию эти атрибуты могут возвращаться методом [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) .  
  
 Элемент [AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md) управляет автоматическим созданием статистических схем для атрибута службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Элемент **AggregationUsage** не ограничивает любые статистические обработки, созданные для куба вручную.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
