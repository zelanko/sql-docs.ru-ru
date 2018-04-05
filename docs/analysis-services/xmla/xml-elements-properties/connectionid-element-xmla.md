---
title: Элемент ConnectionID (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a8a8ec3a265b709415fd9e1a2554513cc9a0751d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="connectionid-element-xmla"></a>Элемент ConnectionID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Определяет активное соединение, на котором выполняется родительский [отменить](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Отмена](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Элемент CancelAssociated &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Элемент SessionID &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Элемент SPID &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
