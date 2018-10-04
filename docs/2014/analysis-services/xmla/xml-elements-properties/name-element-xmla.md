---
title: Назовите элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 422bd152e82a471ce0f130a26aaa12a56026419a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127904"
---
# <a name="name-element-xmla"></a>Элемент Name (XML для аналитики)
  Содержит имя элемента атрибута для родительского [атрибут](attribute-element-xmla.md) или [перевода](translation-element-xmla.md) элемент.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Предок или родитель:|Количество элементов|  
|[Attribute](attribute-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|[Перевод](translation-element-xmla.md)|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибут](attribute-element-xmla.md), [перевода](translation-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `Attribute` элемент `Name` содержит имя элемента атрибута, которое будет вставлено или обновлено командой `Insert` или `Update` соответственно.  
  
 Для элементов `Translation` элемент `Name` содержит заголовок элемента атрибута на языке, указанном в элементе `Language` родительского объекта `Translation`. Если элемент `Name` не указан или содержит пустую строку, используется значение элемента `Name` для элемента `Attribute`, который содержит элемент `Translation`.  
  
## <a name="see-also"></a>См. также  
 [Вставка элемента &#40;XML для Аналитики&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Языковой элемент &#40;XML для Аналитики&#41;](language-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
