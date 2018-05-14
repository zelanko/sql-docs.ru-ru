---
title: Элемент ReadDefinition (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 566190775f9247f253ae614876d3b011dea604b7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="readdefinition-element-assl"></a>Элемент ReadDefinition (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, могут ли элементы читать определение базы данных или определение объектов в базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Permission> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <ReadDefinition>...</ReadDefinition>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md), [DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission ](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md), [Разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*None*|Доступ к определению объекта не разрешен.|  
|*Basic*|Разрешен базовый доступ к определению объекта.<br /><br /> Примечание: Это разрешение требуется для создания локальных кубов, связывания групп мер и связывания измерений.|  
|*Допускается*|Разрешен полный доступ к определению объекта.<br /><br /> Примечание: Это разрешение требуется для выполнения [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) XML для аналитики (XMLA) вызова, с помощью параметра DISCOVER_XML_METADATA.|  
  
 Элементы, соответствующие родителям элемента **ReadDefinition** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubePermission>, <xref:Microsoft.AnalysisServices.DatabasePermission>, <xref:Microsoft.AnalysisServices.DimensionPermission>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, <xref:Microsoft.AnalysisServices.MiningStructurePermission>и <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
