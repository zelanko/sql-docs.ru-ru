---
title: Тип данных Binding (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Binding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- BINDING
helpviewer_keywords:
- Binding data type
ms.assetid: 0a777219-b885-4961-ac66-b76faeb520db
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e46d48f94035a59c54a3e9bb9c8ccb087226660
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135904"
---
# <a name="binding-data-type-assl"></a>Тип данных Binding (ASSL)
  Определяет абстрактный примитивный тип данных, представляющий связь зависимости между двумя объектами, в которых данные или метаданные одного объекта зависят от данных или метаданных привязанного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[AttributeBinding](binding-data-type-assl.md), [ColumnBinding](columnbinding-data-type-assl.md), [CubeAttributeBinding](cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), [InheritedBinding](inheritedbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), [MeasureGroupBinding](measuregroupbinding-data-type-assl.md), [ MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md), [RowBinding](rowbinding-data-type-assl.md), [TabularBinding](tabularbinding-data-type-assl.md), [ TimeAttributeBinding](timeattributebinding-data-type-assl.md), [TimeBinding](timebinding-data-type-assl.md), [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Binding>.  
  
 Дополнительные сведения о привязке данных см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Элементы типа Binding  
 В следующей таблице приведены элементы типа `Binding`.  
  
|Родительский элемент|Элемент типа `Binding`|Комментарии|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../properties/source-element-binding-assl.md) из [CaptionColumn](../objects/column-element-assl.md) (типа [DataItem](dataitem-data-type-assl.md))|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md) или [ColumnBinding](columnbinding-data-type-assl.md)|  
|[Cube](../objects/cube-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (вне строки)](../objects/group-element-assl.md)|Тип `Binding` должно быть [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[DataItem](dataitem-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Элемент `Binding` может быть любого типа|  
|[Dimension](../objects/dimension-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), или [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](dimensionattribute-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md) или [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](action-data-type-assl.md)|[Столбец](../objects/column-element-assl.md)|Тип `Binding` должно быть [CubeAttributeBinding](cubeattributebinding-data-type-assl.md) или [MeasureBinding](measurebinding-data-type-assl.md)|  
|[Меры](../objects/measure-element-assl.md)|[Источник](../properties/source-element-binding-assl.md) (типа [DataItem](dataitem-data-type-assl.md))|Тип `Binding` должно быть [ColumnBinding](columnbinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), или [RowBinding](rowbinding-data-type-assl.md)|  
|[Группа мер](../objects/measuregroup-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[Источник](../properties/source-element-binding-assl.md) из [KeyColumn](../objects/keycolumn-element-assl.md) (типа [DataItem](dataitem-data-type-assl.md))|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md) или [ColumnBinding](columnbinding-data-type-assl.md), или [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки)](measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../objects/dimension-element-assl.md)|Тип `Binding` должно быть [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки)](measuregroupbinding-data-type-out-of-line-assl.md)|[Меры](../objects/measure-element-assl.md)|Тип `Binding` должно быть [MeasureBinding](measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки)](../objects/partition-element-assl.md)|Тип `Binding` должно быть [PartitionBinding](partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки)](measuregroupbinding-data-type-out-of-line-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [TableBinding](tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](dimension-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), или [DimensionBinding](dimensionbinding-data-type-assl.md)|  
|[Секция](../objects/partition-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [TabularBinding](tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md), [тип данных CubeAttributeBinding &#40;ASSL&#41;](cubeattributebinding-data-type-assl.md), или [тип данных MeasureBinding &#40;ASSL&#41;](measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/sourcemeasuregroup-element-assl.md)|Тип `Binding` должно быть [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
