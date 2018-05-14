---
title: Элемент DesignAggregations (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5338f7650cdd1f533832987f5fe79a532a9a375d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="designaggregations-element-xmla"></a>Элемент DesignAggregations (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Дочерние элементы|[Материализовать](../../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md), [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [оптимизации](../../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md), [запросы](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md), [действия](../../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md), [хранения](../../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md) , [Времени](../../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда **DesignAggregations** используется для создания определений агрегатов, хранимых в статистической схеме. Затем статистическая схема может использоваться при материализации агрегатов для секции и повторно применяться в других секциях.  
  
## <a name="see-also"></a>См. также  
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
