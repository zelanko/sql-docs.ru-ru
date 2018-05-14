---
title: Элемент SessionID (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ebda55754f2a6613c3f69347d2ad418796dd4358
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="sessionid-element-xmla"></a>Элемент SessionID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Идентифицирует активный сеанс, в котором выполняется родительский элемент [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cancel>  
   ...  
   <SessionID>...</SessionID>  
   ...  
</Cancel>  
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
|Родительские элементы|[Отмена](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Элемент CancelAssociated & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Элемент ConnectionID & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Элемент SPID & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
