---
title: Имя элемента (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
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
ms.openlocfilehash: c55d77106acf56bf8f94439fdd4dd68a7cfb4fda
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="name-element-xmla"></a>Элемент Name (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит имя элемента атрибута для родительского [атрибута](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) или [перевода](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|См. таблицу ниже.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Атрибут](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|[Перевод](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибут](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [перевода](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Для **атрибута** элементов, **имя** элемент содержит имя элемента атрибута, чтобы вставлять или обновлять во время выполнения, соответственно, **вставить** или **Обновления** команды.  
  
 Для **перевода** элементов, **имя** элемент содержит заголовок элемента атрибута, в языке, указанном в **язык** родителя **Перевод** объекта. Если **имя** элемент не указан или является пустой строкой, значение **имя** элемент для **атрибута** элемент, содержащий  **Перевод** используется элемент.  
  
## <a name="see-also"></a>См. также  
 [Вставить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент языка &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Обновить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
