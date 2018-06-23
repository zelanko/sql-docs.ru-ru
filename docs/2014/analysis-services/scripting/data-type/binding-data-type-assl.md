---
title: Тип данных Binding (ASSL) | Документы Microsoft
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
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 24847c70a0baf6ee12c1de6364cdd1e8d4327f91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191304"
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
|Производные типы данных|[AttributeBinding](binding-data-type-assl.md), [ColumnBinding](columnbinding-data-type-assl.md), [CubeAttributeBinding](cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), [InheritedBinding](inheritedbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), [MeasureGroupBinding](measuregroupbinding-data-type-assl.md), [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md), [RowBinding](rowbinding-data-type-assl.md), [TabularBinding](tabularbinding-data-type-assl.md), [TimeAttributeBinding](timeattributebinding-data-type-assl.md), [TimeBinding](timebinding-data-type-assl.md), [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Binding>.  
  
 Дополнительные сведения о привязке данных см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Элементы типа Binding  
 В следующей таблице приведены элементы типа `Binding`.  
  
|Родительский элемент|Элемент типа `Binding`|Комментарии|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../properties/source-element-binding-assl.md) из [CaptionColumn](../objects/column-element-assl.md) (типа [DataItem](dataitem-data-type-assl.md))|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md) или [ColumnBinding](columnbinding-data-type-assl.md)|  
|[Cube](../objects/cube-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (вне строки.)](../objects/group-element-assl.md)|Тип `Binding` должно быть [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[DataItem](dataitem-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Элемент `Binding` может быть любого типа|  
|[Dimension](../objects/dimension-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), или [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](dimensionattribute-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md) или [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](action-data-type-assl.md)|[Столбец](../objects/column-element-assl.md)|Тип `Binding` должно быть [CubeAttributeBinding](cubeattributebinding-data-type-assl.md) или [MeasureBinding](measurebinding-data-type-assl.md)|  
|[Меры](../objects/measure-element-assl.md)|[Источник](../properties/source-element-binding-assl.md) (типа [DataItem](dataitem-data-type-assl.md))|Тип `Binding` должно быть [ColumnBinding](columnbinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), или [RowBinding](rowbinding-data-type-assl.md)|  
|[Группа мер](../objects/measuregroup-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[Источник](../properties/source-element-binding-assl.md) из [KeyColumn](../objects/keycolumn-element-assl.md) (типа [DataItem](dataitem-data-type-assl.md))|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md) или [ColumnBinding](columnbinding-data-type-assl.md), или [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../objects/dimension-element-assl.md)|Тип `Binding` должно быть [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](measuregroupbinding-data-type-out-of-line-assl.md)|[Меры](../objects/measure-element-assl.md)|Тип `Binding` должно быть [MeasureBinding](measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](../objects/partition-element-assl.md)|Тип `Binding` должно быть [PartitionBinding](partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (вне строки.)](measuregroupbinding-data-type-out-of-line-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [TableBinding](tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](dimension-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), или [DimensionBinding](dimensionbinding-data-type-assl.md)|  
|[Секция](../objects/partition-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [TabularBinding](tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Тип `Binding` должно быть [AttributeBinding](binding-data-type-assl.md), [тип данных CubeAttributeBinding &#40;ASSL&#41;](cubeattributebinding-data-type-assl.md), или [MeasureBinding, тип данных &#40;ASSL&#41;](measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/sourcemeasuregroup-element-assl.md)|Тип `Binding` должно быть [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  