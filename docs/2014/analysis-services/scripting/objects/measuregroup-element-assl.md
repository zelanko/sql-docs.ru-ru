---
title: Элемент MeasureGroup (ASSL) | Документация Майкрософт
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
- MeasureGroup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroup
helpviewer_keywords:
- MeasureGroup element
ms.assetid: 7aa099db-5dc7-4cac-b437-f73fc0921b24
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee73b594fde5e3a9e915615d1a343296ce846d52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163375"
---
# <a name="measuregroup-element-assl"></a>Элемент MeasureGroup (ASSL)
  Определяет набор мер на одном уровне гранулярности.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroups>  
   <MeasureGroup> <!-- ancestor: Cube -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</<Create  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Type>...</Type>  
      <State>...</State>  
      <MeasureQualification>...</MeasureQualification>  
      <Measures>...</Measures>  
      <DataAggregation>...</DataAggregation>  
      <Source>...</Source>  
            <StorageMode>...</StorageMode>  
      <StorageLocation>...</StorageLocation>  
      <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
            <ProactiveCaching>...</ProactiveCaching>  
      <EstimatedRows>...</EstimatedRows>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <EstimatedSize>...</EstimatedSize>  
      <ProcessingMode>...</ProcessingMode>  
      <Dimensions>...</Dimensions>  
      <Partitions>...</Partitions>  
      <AggregationPrefix>...</AggregationPrefix>  
      <ProcessingPriority>...</ProcessingPriority>  
            <AggregationDesigns>...</AggregationDesigns>  
      <Annotations>...</Annotations>  
   </MeasureGroup>  
   <!-- or  -->  
   <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- ancestor: CubeBinding -->  
   <!-- or  -->  
   <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- ancestor: Perspective -->  
</MeasureGroups>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|None|  
|[CubeBinding](../data-type/binding-data-type-assl.md)|  
|[Перспективы](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MeasureGroups](../collections/groups-element-assl.md)|  
|Дочерние элементы||  
  
|Предок или родитель|Дочерние элементы|  
|------------------------|--------------------|  
|[Куб](../collections/aggregationdesigns-element-assl.md), [AggregationPrefix](../properties/aggregationprefix-element-assl.md), [заметки](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DataAggregation](aggregation-element-assl.md), [ Описание](../properties/description-element-assl.md), [измерения](../collections/dimensions-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [EstimatedSize](../properties/estimatedsize-element-assl.md), [Идентификатор](../properties/id-element-assl.md), [IgnoreUnrelatedDimensions](../properties/ignoreunrelateddimensions-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ MeasureQualification](../properties/measurequalificaton-element-assl.md), [меры](../collections/measures-element-assl.md), [имя](../properties/name-element-assl.md), [секций](../collections/partitions-element-assl.md), [ProactiveCaching](proactivecaching-element-assl.md), [ ProcessingMode](../properties/processingmode-element-assl.md), [ProcessingPriority](../properties/processingpriority-element-assl.md), [источника](../properties/source-element-measure-assl.md), [состояние](../properties/state-element-assl.md), [StorageLocation](../properties/storagelocation-element-assl.md), [ StorageMode](../properties/storagemode-element-assl.md), [переводы](../collections/translations-element-assl.md), [типа](../properties/type-element-measuregroup-assl.md)|  
|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)|None|  
|[Перспективы](perspective-element-assl.md)|None|  
  
## <a name="remarks"></a>Примечания  
 Все меры в группе мер должны происходить из одной таблицы. Группа мер может определить привязки по умолчанию, которые могут быть изменены для каждой секции.  
  
 Элемент `MeasureGroup` определяет сведения, общие для групп мер обычных и виртуальных кубов. Сведения, специфические для каждого типа, определяются отдельными подтипами.  
  
 Свойство `State` элемента `MeasureGroup` имеет следующие значения.  
  
-   *FullyProcessed* , если обрабатываются все секции.  
  
-   *PartiallyProcessed* , если обрабатывается как минимум одна секция.  
  
-   *Unprocessed* , если не обрабатывается ни одной секции.  
  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.MeasureGroup> и <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
