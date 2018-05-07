---
title: Тип данных MeasureGroupDimension (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28fca75a28d3b717763f032f64b40afaaf8f401f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="measuregroupdimension-data-type-assl"></a>Тип данных MeasureGroupDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет абстрактный примитивный тип данных, представляющий связь между измерением и группой мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroupDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
      <Annotations>...</Annotations>  
   <Source>...</Source>  
</MeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[DataMiningMeasureGroupDimension](../../../analysis-services/scripting/data-type/dataminingmeasuregroupdimension-data-type-assl.md), [DegenerateMeasureGroupDimension](../../../analysis-services/scripting/data-type/degeneratemeasuregroupdimension-data-type-assl.md), [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md), [ReferenceMeasureGroupDimension](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md), [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md), [Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|Производные элементы|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md) (коллекция[Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md) элемента [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Каждый элемент **MeasureGroupDimension** — это ссылка на одно из измерений куба. Они определяют, какие измерения куба применяются к группе мер.  
  
 Набор предоставленных атрибутов определяет гранулярность (область), в которой известны меры из группы мер. Например, меры, которые представляют продажи продуктов, содержатся в группе мер «Sales». Информация об этих мерах хранится в базовом источнике данных с гранулярностью по месяцам, а не по неделям или дням. В этом случае для элемента **MeasureGroupDimension** , описывающего связь между измерением времени и группой мер «Sales», будет перечислен только атрибут «Month». В редких случаях гранулярность может определяться набором атрибутов. Например, если дан набор атрибутов {Day, Week, Month, Year}, в котором день подразумевает неделю и месяц, но неделя не подразумевает месяц, то меры, содержащиеся в группе мер Forecasts, могут быть известны по месяцам и неделям, но не по дням.  
  
 Если атрибуты не были предоставлены, это равнозначно тому, что для измерения был перечислен только ключевой атрибут (определяя самый нижний уровень гранулярности). Каждая секция в группе мер должна иметь одинаковую гранулярность. Набор перечисленных атрибутов не должен быть избыточным в плане связей между атрибутами. Например, если месяц подразумевает год, то гранулярность следует определить как месяц, а не как месяц и год.  
  
 Элемент **MeasureGroupDimension** должен включать иерархию только в том случае, если она должна отображать что-то конкретное о нем (нельзя выбрать, какие именно иерархии будут применены к определенной группе мер). Также он должен включать элемент [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md) только в том случае, если он должен отображать что-то конкретное о нем.  
  
 Каждая иерархия должна быть подмножеством иерархий, включенных в элемент [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md). Выбрать уровни невозможно, хотя некоторые из них могут быть автоматически отключены в зависимости от гранулярности группы мер.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MeasureGroupDimension>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
