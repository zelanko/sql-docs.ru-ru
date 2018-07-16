---
title: Элемент Events (ASSL) | Документация Майкрософт
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
- Events Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Events
helpviewer_keywords:
- Events element
ms.assetid: de887998-dc4b-44dc-8fec-08d67b92f96d
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 33f6d302557369d7cbc90c1d5786bc21d37b0f42
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293504"
---
# <a name="events-element-assl"></a>Элемент Events (ASSL)
  Определяет коллекцию элементов [Event](../objects/event-element-assl.md) , которые будет отслеживать трассировка [Trace](../objects/trace-element-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
   ...  
   <Events>  
      <Event>...</Event>  
   </Events>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Trace](../objects/trace-element-assl.md)|  
|Дочерние элементы|[Событие](../objects/event-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.TraceEventCollection>.  
  
## <a name="see-also"></a>См. также  
 [Выполняет трассировку элемент &#40;ASSL&#41;](traces-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
