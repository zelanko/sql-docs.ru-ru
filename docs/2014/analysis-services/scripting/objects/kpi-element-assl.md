---
title: Элемент KPI (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Kpi Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpi
helpviewer_keywords:
- Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 63b7947785976d41cda112b1c14b3829e3f98e3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124154"
---
# <a name="kpi-element-assl"></a>Элемент Kpi (ASSL)
  Определяет ключевой показатель эффективности (KPI) в пределах [куба](cube-element-assl.md) элемент или [перспективы](perspective-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Kpis>  
   <Kpi> <!-- ancestor: Cube -->  
            <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DisplayFolder>...</DisplayFolder>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <Value>...</Value>  
            <Goal>...</Goal>  
      <Status>...</Status>  
      <Trend>...</Trend>  
      <TrendGraphic>...</TrendGraphic>  
      <StatusGraphic>...</StatusGraphic>  
      <CurrentTimeMember>...</CurrentTimeMember>  
      <Annotations>...</Annotations>  
   </Kpi>  
   <!-- or -->  
   <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- ancestor: Perspective -->  
   </Kpi>  
</Kpis>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|None|  
|[Перспективы](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Ключевые показатели эффективности](../collections/kpis-element-assl.md)|  
  
## <a name="child-elements"></a>Дочерние элементы  
  
|Предок или родитель|Дочерние элементы|  
|------------------------|--------------------|  
|[Куб](../collections/annotations-element-assl.md), [AssociatedMeasureGroupID](../properties/id-element-assl.md), [CurrentTimeMember](member-element-assl.md), [описание](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Цель](../properties/goal-element-assl.md), [идентификатор](../properties/id-element-assl.md), [имя](../properties/name-element-assl.md), [состояние](../properties/status-element-assl.md), [StatusGraphic](../properties/statusgraphic-element-assl.md), [переводы ](../collections/translations-element-assl.md), [Тренда](../properties/trend-element-assl.md), [TrendGraphic](../properties/trendgraphic-element-assl.md), [значение](../properties/value-element-assl.md)|  
|[Перспективы](perspective-element-assl.md)|None|  
  
## <a name="remarks"></a>Примечания  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.Kpi> и <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
