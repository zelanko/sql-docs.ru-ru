---
title: Ключ элемента (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Key Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5bdcc944f91730aedfce261a9602a5198b65c9a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="key-element-xmla"></a>Элемент Key (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Родительские элементы|[Ключи](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Используемый этим элементом тип данных должен соответствовать типу данных надлежащего ключевого столбца указанного атрибута. Если для родителя **Key** элементы **Attribute** не указаны, то для определения модифицируемых элементов атрибута используются элементы **AttributeName** и **Name** , указанные в родительском элементе **Attribute** .  
  
## <a name="see-also"></a>См. также  
 [Элемент Attribute & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [Элемент AttributeName & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Удалить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Вставить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент KeyColumn & #40; ASSL & #41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Обновить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Где элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
