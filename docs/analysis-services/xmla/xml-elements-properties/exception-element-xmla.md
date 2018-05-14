---
title: Элемент Exception (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91350ba6e82e070707d17b58c82bf305c1e87660
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="exception-element-xmla"></a>Элемент Exception (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, что исключение было вернуть из [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
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
  
## <a name="remarks"></a>Примечания  
 Если во время выполнения метода **Discover** или отдельной команды XMLA при вызове метода **Execute** возникает ошибка, препятствующая завершению команды или метода, элемент **root** для этого метода или команды содержит элемент **Exception** и элемент **Messages** . Элемент **Exception** указывает на ошибку, вследствие которой метод или команда завершилась неудачей, а элемент **Messages** содержит список ошибок или предупреждений, связанных с этой ошибкой.  
  
## <a name="see-also"></a>См. также  
 [Сообщения элемент &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
