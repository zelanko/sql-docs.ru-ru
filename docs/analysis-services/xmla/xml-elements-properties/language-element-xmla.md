---
title: "Элемент языка (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Language Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Language
- microsoft.xml.analysis.language
- http://schemas.microsoft.com/analysisservices/2003/engine#Language
helpviewer_keywords:
- Language element
ms.assetid: cd998202-e43f-4c6c-8727-a15a76a520ea
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2410bfc2c98947f2ebe7144483e2f53bbb28d527
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="language-element-xmla"></a>Элемент Language (XML для аналитики)
  Содержит идентификатор языка (LCID) для родительского [перевода](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Translation>  
   ...  
   <Language>...</Language>  
   ...  
</Translation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Перевод](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Язык** элемент указывает код языка, используемый родительским **перевода** элемента, который требуется назначить **имя** родителя **перевода** элемент для элемента атрибута для указанного языка, во время **вставить** или **обновление** команды.  
  
## <a name="see-also"></a>См. также:  
 [Вставить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент Name &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)   
 [Обновить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

