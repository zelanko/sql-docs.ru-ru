---
title: Ключ элемента (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Key Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1f98ae6863f0aab25149ee4f8a69ef13b65da974
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213764"
---
# <a name="key-element-xmla"></a>Элемент Key (XML для аналитики)
  Содержит значение ключа элемента для элемента атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Любой|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Ключи](keys-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Используемый этим элементом тип данных должен соответствовать типу данных надлежащего ключевого столбца указанного атрибута. Если для родителя `Key` элементы `Attribute` не указаны, то для определения модифицируемых элементов атрибута используются элементы `AttributeName` и `Name`, указанные в родительском элементе `Attribute`.  
  
## <a name="see-also"></a>См. также  
 [Атрибут элемента &#40;XML для Аналитики&#41;](attribute-element-xmla.md)   
 [Элемент AttributeName &#40;XML для Аналитики&#41;](name-element-xmla.md)   
 [Элемент DROP &#40;XML для Аналитики&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [Вставка элемента &#40;XML для Аналитики&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Элемент KeyColumn &#40;ASSL&#41;](../../scripting/objects/column-element-assl.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Где элемент &#40;XML для Аналитики&#41;](where-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
