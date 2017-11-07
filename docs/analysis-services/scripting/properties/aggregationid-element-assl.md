---
title: "Элемент AggregationID (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AggregationID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AggregationID element
ms.assetid: 6056da1d-b6b4-4074-84db-45be719df49a
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 839014c19a80b8689d4a94178c25af7fb4c673c8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationid-element-assl"></a>Элемент AggregationID (ASSL)
  Идентифицирует определение агрегата из [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) элемент, используемый для создания экземпляра агрегата.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationInstance>  
   ...  
   <AggregationID>...</AggregationID>  
   ...  
</AggregationInstance>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Если данный элемент отсутствует или содержит пустую строку, то элемент **AggregationInstance** представляет пользовательский агрегат.  
  
 Элемент, соответствующий родителю параметра **AggregationID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

