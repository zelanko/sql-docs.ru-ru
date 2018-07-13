---
title: Элемент Description (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Description Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Description
helpviewer_keywords:
- Description element
ms.assetid: 34d67e7c-e79a-429b-8cc3-6ca13b9cf9c3
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dadef861a5b54dafddd6f2dcf3072cd4e0d510ad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194134"
---
# <a name="description-element-assl"></a>Элемент Description (ASSL)
  Содержит описание родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Description>...</Description>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действие](../objects/action-element-assl.md), [статистической обработки](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [сборки](../objects/assembly-element-assl.md), [AttributePermission](../objects/attributepermission-element-assl.md), [ CalculationProperty](../objects/calculationproperty-element-assl.md), [CellPermission](../objects/cellpermission-element-assl.md), [куба](../objects/cube-element-assl.md), [CubeDimensionPermission](../data-type/permission-data-type-assl.md), [базы данных](../objects/database-element-assl.md) , [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [измерения](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [иерархии](../objects/hierarchy-element-assl.md), [Ключевого показателя эффективности](../objects/kpi-element-assl.md), [уровень](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [мер](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [ Раздел](../objects/partition-element-assl.md), [разрешение](../data-type/permission-data-type-assl.md), [перспективы](../objects/perspective-element-assl.md), [роли](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [ Трассировки](../objects/trace-element-assl.md), [перевода](../objects/translation-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 На значение элемента `Description` накладываются следующие ограничения.  
  
-   Значение не может содержать начальные или конечные пробелы. Если начальные или конечные пробелы будут включены в значение `Description` элемента, эти пробелы будут неявно удалены службой [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Значение не может содержать управляющие символы. Если в значении элемента `Description` содержатся управляющие символы, они будут неявно удалены службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Назовите элемент &#40;ASSL&#41;](name-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
