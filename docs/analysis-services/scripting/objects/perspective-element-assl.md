---
title: Элемент perspective (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d84b369134c55a09317ae8812f2d511e147605bf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="perspective-element-assl"></a>Элемент Perspective (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет подробные сведения для перспективы элемента [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Перспективы](../../../analysis-services/scripting/collections/perspectives-element-assl.md)|  
|Дочерние элементы|[Действия](../../../analysis-services/scripting/collections/actions-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [вычисления](../../../analysis-services/scripting/collections/calculations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [DefaultMeasure](../../../analysis-services/scripting/properties/defaultmeasure-element-assl.md), [ Описание](../../../analysis-services/scripting/properties/description-element-assl.md), [измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [ключевые показатели эффективности](../../../analysis-services/scripting/collections/kpis-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [ MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [переводов](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Перспектива предоставляет подмножество куба путем выбора измерений, иерархий, атрибутов и других подробностей, которые необходимо включить, а также определением среза необходимых для включения данных. Перспективой владеет конкретный куб. Нельзя переопределить или добавить объекты в рамках перспективы; все измерения, иерархии и другие сведения должны существовать в базовом кубе. Нельзя включить объекты и отметить их как невидимые.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>См. также  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
