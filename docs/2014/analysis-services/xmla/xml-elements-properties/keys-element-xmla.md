---
title: Ключи элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Keys Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Keys
- http://schemas.microsoft.com/analysisservices/2003/engine#Keys
- microsoft.xml.analysis.keys
helpviewer_keywords:
- Keys element
ms.assetid: 67291791-0032-412a-9a4f-74f68533e83d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 48065d8c40c6cba3b60d405be77d0e1877e11910
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148714"
---
# <a name="keys-element-xmla"></a>Элемент Keys (XML для аналитики)
  Содержит коллекцию [ключ](key-element-xmla.md) элементы, используемые для идентификации ключей элементов, принадлежащих элементу атрибута, представленного родительским [атрибут](attribute-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute>  
   ...  
   <Keys>  
      <Key>...</Key>  
   </Keys>  
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
|Дочерние элементы|[Key](key-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Элемент DROP &#40;XML для Аналитики&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [Вставка элемента &#40;XML для Аналитики&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
