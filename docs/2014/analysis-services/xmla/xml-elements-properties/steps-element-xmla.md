---
title: Шаги элемент (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Steps Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Steps
- microsoft.xml.analysis.steps
- urn:schemas-microsoft-com:xml-analysis#Steps
helpviewer_keywords:
- Steps element
ms.assetid: a6821a2a-89ec-418b-b2dd-92adf2ccc20e
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cfafdc9aa9644b028d66b844550175a462a0258a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194108"
---
# <a name="steps-element-xmla"></a>Элемент Steps (XML для аналитики)
  Определяет максимальное число шагов, используемых командой [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) при построении статистических выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DesignAggregations>  
   ...  
   <Steps>...</Steps>  
   ...  
</DesignAggregations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  