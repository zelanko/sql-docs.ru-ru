---
title: "Элемент Exception (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Exception Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0c83900d85d698c5f9b2c0bdca2c197ab4ce05b1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="exception-element-xmla"></a>Элемент Exception (XML для аналитики)
  Указывает, что исключение было вернуть из [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен**`http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Если во время выполнения метода **Discover** или отдельной команды XMLA при вызове метода **Execute** возникает ошибка, препятствующая завершению команды или метода, элемент **root** для этого метода или команды содержит элемент **Exception** и элемент **Messages** . Элемент **Exception** указывает на ошибку, вследствие которой метод или команда завершилась неудачей, а элемент **Messages** содержит список ошибок или предупреждений, связанных с этой ошибкой.  
  
## <a name="see-also"></a>См. также:  
 [Элемент messages &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

