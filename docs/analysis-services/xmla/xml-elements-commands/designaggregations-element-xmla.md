---
title: "Элемент DesignAggregations (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DesignAggregations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords: DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d442725b09919ef9cbbec87cc08c0e01551bc5ae
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="designaggregations-element-xmla"></a>Элемент DesignAggregations (XML для аналитики)
  Создает агрегаты для статистической схемы в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <DesignAggregations>  
      <Object>...</Object>  
      <Time>...</Time>  
      <Steps>...</Steps>  
      <Optimization>...</Optimization>  
      <Storage>...</Storage>  
      <Materialize>...</Materialize>  
      <Queries>...</Queries>  
   </DesignAggregations>  
</Command>  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Материализовать](../../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md), [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [оптимизации](../../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md), [запросы](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md), [действия](../../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md), [хранения](../../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md), [Времени](../../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Команда **DesignAggregations** используется для создания определений агрегатов, хранимых в статистической схеме. Затем статистическая схема может использоваться при материализации агрегатов для секции и повторно применяться в других секциях.  
  
## <a name="see-also"></a>См. также:  
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
