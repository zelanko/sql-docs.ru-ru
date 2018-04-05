---
title: Элемент perspective (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
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
- Perspective Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 424139e88f88ee4c3e3073997bf8724c4534ba1c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="perspective-element-assl"></a>Элемент Perspective (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет подробные сведения для перспективы элемента [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.  
  
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
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Перспективы](../../../analysis-services/scripting/collections/perspectives-element-assl.md)|  
|Дочерние элементы|[Действия](../../../analysis-services/scripting/collections/actions-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [вычисления](../../../analysis-services/scripting/collections/calculations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [DefaultMeasure](../../../analysis-services/scripting/properties/defaultmeasure-element-assl.md), [ Описание](../../../analysis-services/scripting/properties/description-element-assl.md), [измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [ключевые показатели эффективности](../../../analysis-services/scripting/collections/kpis-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [ MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [переводов](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Перспектива предоставляет подмножество куба путем выбора измерений, иерархий, атрибутов и других подробностей, которые необходимо включить, а также определением среза необходимых для включения данных. Перспективой владеет конкретный куб. Нельзя переопределить или добавить объекты в рамках перспективы; все измерения, иерархии и другие сведения должны существовать в базовом кубе. Нельзя включить объекты и отметить их как невидимые.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
