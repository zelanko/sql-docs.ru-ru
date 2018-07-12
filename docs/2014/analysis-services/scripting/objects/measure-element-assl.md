---
title: Измерить элемент (ASSL) | Документация Майкрософт
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
- Measure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80d59a5356bf1c0b5712e729f230fff9383603cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159335"
---
# <a name="measure-element-assl"></a>Элемент Measure (ASSL)
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
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[Группа мер](group-element-assl.md)|None|  
|[MeasureGroupBinding (вне строки)](../data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Меры](../collections/measures-element-assl.md)|  
  
|Предок или родитель|Дочерние элементы|  
|------------------------|--------------------|  
|[MeasureGroup](../properties/aggregatefunction-element-assl.md), [заметки](../collections/annotations-element-assl.md), [BackColor](../properties/backcolor-element-assl.md), [DataType](../properties/datatype-element-assl.md), [описание](../properties/description-element-assl.md), [DisplayFolder ](../properties/displayfolder-element-assl.md), [FontFlags](../properties/fontflags-element-assl.md), [FontName](../properties/name-element-assl.md), [FontSize](../properties/fontsize-element-assl.md), [ForeColor](../properties/forecolor-element-assl.md), [FormatString ](../properties/formatstring-element-assl.md), [Идентификатор](../properties/id-element-assl.md), [MeasureExpression](../properties/expression-element-assl.md), [имя](../properties/name-element-assl.md), [источника](../properties/source-element-measure-assl.md), [переводы](../collections/translations-element-assl.md), [Видимым](../properties/visible-element-assl.md)|  
|Все остальные|None|  
  
## <a name="remarks"></a>Примечания  
 Для меры могут быть предоставлены подробности привязки. Эти подробности затем действуют в качестве значений по умолчанию для секций.  
  
 В более крупных кубах могут существовать сотни мер и иерархий. Свойство `DisplayFolder` определяет внешний вид для пользователя на клиенте. Возможен любой из следующих вариантов значения свойства `DisplayFolder`.  
  
-   Пустое значение означает, что мера не принадлежит папке.  
  
-   Одно имя папки означает, что мера должна обрабатываться как принадлежащая папке с таким же именем.  
  
-   Несколько имен папок, разделенных обратной косой черты (\\), обозначающая иерархию вложенных папок.  
  
 Свойство `DisplayFolder` применяется также для вычисляемых мер и иерархий.  
  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.Measure> и <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
