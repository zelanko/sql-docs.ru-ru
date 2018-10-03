---
title: Элемент DesignAggregations (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DesignAggregations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords:
- DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c9ddcd70a0512273f816b633933b26fbf12d5b5a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058994"
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
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Материализация](../xml-elements-properties/materialize-element-xmla.md), [объект](../xml-elements-properties/object-element-xmla.md), [оптимизации](../xml-elements-properties/optimization-element-xmla.md), [запросы](../xml-elements-properties/queries-element-xmla.md), [действия](../xml-elements-properties/steps-element-xmla.md), [хранения](../xml-elements-properties/storage-element-xmla.md) , [Времени](../xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `DesignAggregations` используется для создания определений агрегатов, хранимых в статистической схеме. Затем статистическая схема может использоваться при материализации агрегатов для секции и повторно применяться в других секциях.  
  
## <a name="see-also"></a>См. также  
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
