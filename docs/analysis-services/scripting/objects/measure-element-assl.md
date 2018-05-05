---
title: Измерения элемента (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- Measure Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 21296ea1c331fa30d3d826fd9f8ca786ad85c176
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="measure-element-assl"></a>Элемент Measure (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет меру.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Measures>  
   <Measure> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <AggregateFunction>...</AggregateFunction>  
            <DataType>...</DataType>  
            <Source>...</Source>  
      <Visible>...</Visible>  
      <MeasureExpression>...</MeasureExpression>  
      <DisplayFolder>...</DisplayFolder>  
      <FormatString>...</FormatString>  
      <BackColor>...</BackColor>  
      <ForeColor>...</ForeColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Measure>  
   <!-- or  -->  
   <Measure xsi:type="AggregationInstanceMeasure">...</Measure> <!-- parent: AggregationInstance -->  
      <!-- or  -->  
   <Measure xsi:type="MeasureBinding">...</Measure> <!-- ancestor: MeasureGroupBinding (out-of-line) -->  
   <!-- or  -->  
   <Measure xsi:type="PerspectiveMeasure">...</Measure> <!-- ancestor: PerspectiveMeasureGroup -->  
</Measures>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|См. таблицу ниже.|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|[AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|None|  
|[MeasureGroupBinding (вне строки.)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|[PerspectiveMeasure](../../../analysis-services/scripting/data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Меры](../../../analysis-services/scripting/collections/measures-element-assl.md)|  
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок или родитель|Дочерние элементы|  
|------------------------|--------------------|  
|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[AggregateFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [BackColor](../../../analysis-services/scripting/properties/backcolor-element-assl.md), [DataType](../../../analysis-services/scripting/properties/datatype-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md), [FontFlags](../../../analysis-services/scripting/properties/fontflags-element-assl.md), [FontName](../../../analysis-services/scripting/properties/fontname-element-assl.md), [FontSize](../../../analysis-services/scripting/properties/fontsize-element-assl.md), [ForeColor](../../../analysis-services/scripting/properties/forecolor-element-assl.md), [FormatString](../../../analysis-services/scripting/properties/formatstring-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [MeasureExpression](../../../analysis-services/scripting/properties/measureexpression-element-assl.md), [Name](../../../analysis-services/scripting/properties/name-element-assl.md), [Source](../../../analysis-services/scripting/properties/source-element-measure-assl.md), [Translations](../../../analysis-services/scripting/collections/translations-element-assl.md), [Visible](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
|Все остальные|None|  
  
## <a name="remarks"></a>Замечания  
 Для меры могут быть предоставлены подробности привязки. Эти подробности затем действуют в качестве значений по умолчанию для секций.  
  
 В более крупных кубах могут существовать сотни мер и иерархий. Свойство **DisplayFolder** определяет внешний вид для пользователя на клиенте. Возможен любой из следующих вариантов значения свойства **DisplayFolder** .  
  
-   Пустое значение означает, что мера не принадлежит папке.  
  
-   Одно имя папки означает, что мера должна обрабатываться как принадлежащая папке с таким же именем.  
  
-   Несколько имен папок, разделенных обратной косой черты (\\), обозначающий иерархию вложенных папок.  
  
 Свойство **DisplayFolder** применяется также для вычисляемых мер и иерархий.  
  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.Measure> и <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>См. также  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
