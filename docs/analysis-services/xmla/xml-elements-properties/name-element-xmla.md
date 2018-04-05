---
title: Имя элемента (XMLA) | Документы Microsoft
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
- Name Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 995792653603bd7ff5954a34755e7704544675b6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="name-element-xmla"></a>Элемент Name (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Содержит имя элемента атрибута для родительского [атрибута](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) или [перевода](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|См. в следующей таблице.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|[Перевод](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибут](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [перевода](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Для **атрибута** элементов, **имя** элемент содержит имя элемента атрибута, чтобы вставлять или обновлять во время выполнения, соответственно, **вставить** или **Обновления** команды.  
  
 Для **перевода** элементов, **имя** элемент содержит заголовок элемента атрибута, в языке, указанном в **язык** родителя **Перевод** объекта. Если **имя** элемент не указан или является пустой строкой, значение **имя** элемент для **атрибута** элемент, содержащий  **Перевод** используется элемент.  
  
## <a name="see-also"></a>См. также:  
 [Вставить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Языковой элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Обновить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
