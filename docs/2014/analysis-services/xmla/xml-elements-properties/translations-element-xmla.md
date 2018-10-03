---
title: Элемент Translations (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.translations
- urn:schemas-microsoft-com:xml-analysis#Translations
- http://schemas.microsoft.com/analysisservices/2003/engine#Translations
helpviewer_keywords:
- Translations element
ms.assetid: 86fd2119-9bea-4306-829e-cc439da05566
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f216a564f715efbbaa2af2f094d1e4181f8bdbe9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126754"
---
# <a name="translations-element-xmla"></a>Элемент Translations (XML для аналитики)
  Содержит коллекцию элементов [Translation](translation-element-xmla.md) , которые используются для идентификации ключей элементов, принадлежащих элементу атрибута, представленного родительским элементом [Attribute](attribute-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute>  
   ...  
   <Translations>  
      <Translation>...</Translation>  
   </Translations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Attribute](attribute-element-xmla.md)|  
|Дочерние элементы|[Перевод](translation-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Вставка элемента &#40;XML для Аналитики&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
