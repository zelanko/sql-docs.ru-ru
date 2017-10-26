---
title: "Элемент ConnectionID (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ConnectionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ConnectionID
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionID
- microsoft.xml.analysis.connectionid
helpviewer_keywords:
- ConnectionID element
ms.assetid: de044fb2-f713-46b2-8899-14e8d515e823
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 246ac054d937ce49e0f758705ea929f4159a8ccf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="connectionid-element-xmla"></a>Элемент ConnectionID (XML для аналитики)
  Определяет активное соединение, на котором выполняется родительский [отменить](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Отмена](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Элемент CancelAssociated &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Элемент SessionID &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Элемент SPID &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

