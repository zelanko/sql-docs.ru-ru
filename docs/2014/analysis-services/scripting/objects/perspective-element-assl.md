---
title: Элемент perspective (ASSL) | Документация Майкрософт
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
- Perspective Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b006d7d48c072cb98a68e42c04cf75c4aaa9e04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297404"
---
# <a name="perspective-element-assl"></a>Элемент Perspective (ASSL)
  Определяет подробные сведения для перспективы элемента [куба](cube-element-assl.md) элемент.  
  
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
|Родительские элементы|[Перспективы](../collections/perspectives-element-assl.md)|  
|Дочерние элементы|[Действия](../collections/actions-element-assl.md), [заметки](../collections/annotations-element-assl.md), [вычисления](../collections/calculations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultMeasure](measure-element-assl.md), [ Описание](../properties/description-element-assl.md), [измерения](../collections/dimensions-element-assl.md), [идентификатор](../properties/id-element-assl.md), [ключевые показатели эффективности](../collections/kpis-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ MeasureGroups](../collections/groups-element-assl.md), [имя](../properties/name-element-assl.md), [переводы](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Перспектива предоставляет подмножество куба путем выбора измерений, иерархий, атрибутов и других подробностей, которые необходимо включить, а также определением среза необходимых для включения данных. Перспективой владеет конкретный куб. Нельзя переопределить или добавить объекты в рамках перспективы; все измерения, иерархии и другие сведения должны существовать в базовом кубе. Нельзя включить объекты и отметить их как невидимые.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
