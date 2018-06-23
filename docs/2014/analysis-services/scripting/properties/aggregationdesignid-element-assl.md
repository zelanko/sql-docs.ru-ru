---
title: Элемент AggregationDesignID (ASSL) | Документы Microsoft
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
- AggregationDesignID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesignID
helpviewer_keywords:
- AggregationDesignID element
ms.assetid: e7f1f7ae-3169-4c0c-aadb-f7465155d652
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0548685e81b7c98b80e49ea67bdb754cb0dfe887
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102311"
---
# <a name="aggregationdesignid-element-assl"></a>Элемент AggregationDesignID (ASSL)
  Идентифицирует [AggregationDesign](../objects/aggregationdesign-element-assl.md) элемента, связанного с [секции](../objects/partition-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Partition>  
      ...  
   <AggregationDesignID>...</AggregationDesignID>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Секция](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `AggregationDesignID` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Partition>. См. также <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AggregationDesign &#40;ASSL&#41;](../objects/aggregationdesign-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  