---
title: Имя элемента (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f19696ae5eea630a6fe879b603b72c4e955b1ac
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
## <a name="remarks"></a>Примечания  
 Для **атрибута** элементов, **имя** элемент содержит имя элемента атрибута, чтобы вставлять или обновлять во время выполнения, соответственно, **вставить** или **Обновления** команды.  
  
 Для **перевода** элементов, **имя** элемент содержит заголовок элемента атрибута, в языке, указанном в **язык** родителя **Перевод** объекта. Если **имя** элемент не указан или является пустой строкой, значение **имя** элемент для **атрибута** элемент, содержащий  **Перевод** используется элемент.  
  
## <a name="see-also"></a>См. также  
 [Вставить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент языка &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Обновить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
