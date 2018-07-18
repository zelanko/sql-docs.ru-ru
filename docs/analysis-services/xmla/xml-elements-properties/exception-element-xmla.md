---
title: Элемент Exception (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d3e542534b85d0f87b689b196001e9a00fe49b15
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036772"
---
# <a name="exception-element-xmla"></a>Элемент Exception (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, что исключение было возвращено из [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если во время выполнения метода **Discover** или отдельной команды XMLA при вызове метода **Execute** возникает ошибка, препятствующая завершению команды или метода, элемент **root** для этого метода или команды содержит элемент **Exception** и элемент **Messages** . Элемент **Exception** указывает на ошибку, вследствие которой метод или команда завершилась неудачей, а элемент **Messages** содержит список ошибок или предупреждений, связанных с этой ошибкой.  
  
## <a name="see-also"></a>См. также
 [Сообщения элемент &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
