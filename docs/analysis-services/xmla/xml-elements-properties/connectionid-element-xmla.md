---
title: Элемент ConnectionID (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21850935da086387098674eb2df938e7651d1bef
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="connectionid-element-xmla"></a>Элемент ConnectionID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 [Элемент CancelAssociated & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Элемент SessionID & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Элемент SPID & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
