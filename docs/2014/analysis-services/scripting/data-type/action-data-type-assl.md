---
title: Тип данных Action (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Action Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Action data type
ms.assetid: 8c4d2ff7-17e1-4e74-bec7-637e0b191acf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 21c13562fa53c0ba396a4c3826889e8d275f7d9a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197494"
---
# <a name="action-data-type-assl"></a>Тип данных Action (язык ASSL)
  Определяет абстрактный примитивный тип данных, представляющий действие в [куба](../objects/cube-element-assl.md) элемент или [перспективы](../objects/perspective-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Caption>...</Caption>  
      <CaptionIsMdx>...</CaptionIsMdx>  
      <Translations>...</Translations>  
   <TargetType>...</TargetType>  
   <Target>...</Target>  
   <Condition>...</Condition>  
   <Type>...</Type>  
   <Invocation>...</Invocation>  
   <Application>...</Application>  
      <Description>...</Description>  
      <Annotations>...</Annotations>  
</Action>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[DrillThroughAction](action-data-type-assl.md), [ReportAction](reportaction-data-type-assl.md), [StandardAction](standardaction-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действия](../collections/actions-element-assl.md)|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [приложения](../properties/application-element-assl.md), [заголовок](../properties/caption-element-assl.md), [CaptionIsMdx](../properties/captionismdx-element-assl.md), [условие](../properties/condition-element-assl.md), [описание ](../properties/description-element-assl.md), [Идентификатор](../properties/id-element-assl.md), [вызова](../properties/invocation-element-assl.md), [имя](../properties/name-element-assl.md), [целевой](../properties/target-element-assl.md), [TargetType](../properties/targettype-element-assl.md), [Переводы](../collections/translations-element-assl.md), [типа](../properties/type-element-action-assl.md)|  
|Производные элементы|[DrillThroughAction](action-data-type-assl.md), [ReportAction](reportaction-data-type-assl.md), [StandardAction](standardaction-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о действиях см. в разделе [Действия (службы Analysis Services — многомерные данные)](../../multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Элемент куба &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Элемент perspective &#40;ASSL&#41;](../objects/perspective-element-assl.md)   
 [Тип данных PerspectiveAction &#40;ASSL&#41;](perspectiveaction-data-type-assl.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
