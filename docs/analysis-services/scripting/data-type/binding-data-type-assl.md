---
title: Тип данных Binding (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14b216fbc9dffd4cbaade3fd9106e824eebb55c4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="binding-data-type-assl"></a>Тип данных Binding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет абстрактный примитивный тип данных, представляющий связь зависимости между двумя объектами, в которых данные или метаданные одного объекта зависят от данных или метаданных привязанного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md), [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md), [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md), [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md), [TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md), [TimeAttributeBinding](../../../analysis-services/scripting/data-type/timeattributebinding-data-type-assl.md), [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md), [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Binding>.  
  
 Дополнительные сведения о привязке данных см. в разделе [& #40; источники данных и привязки Многомерные службы SSAS & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Элементы типа Binding  
 В следующей таблице приведены элементы типа **Binding**.  
  
|Родительский элемент|Элемент типа **Binding**|Комментарии|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md) [CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md) (типа [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|Тип **привязки** должно быть [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) или [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (вне строки.)](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|Тип **привязки** должно быть [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Элемент**Binding** может быть любого типа|  
|[Измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), или [ TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) или [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|[Столбец](../../../analysis-services/scripting/objects/column-element-assl.md)|Тип **привязки** должно быть [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md) или [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[Меры](../../../analysis-services/scripting/objects/measure-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md) (типа [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|Тип **привязки** должно быть [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), или [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|  
|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md) [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) (типа [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md))|Тип **привязки** должно быть [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) или [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), или [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md)|Тип **привязки** должно быть [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Меры](../../../analysis-services/scripting/objects/measure-element-assl.md)|Тип **привязки** должно быть [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|Тип **привязки** должно быть [PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [MeasureGroupDimensionBinding](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md), или [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|  
|[Секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|Тип **привязки** должно быть [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md), [тип данных CubeAttributeBinding &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md), или [MeasureBinding, тип данных &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[SourceMeasureGroup](../../../analysis-services/scripting/objects/sourcemeasuregroup-element-assl.md)|Тип **привязки** должно быть [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
