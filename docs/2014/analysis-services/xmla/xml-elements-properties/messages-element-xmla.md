---
title: Сообщения, элемент (XMLA) | Документация Майкрософт
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
- Messages Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0fbaba30716831ef34a40dd94c6c9b2ab507641
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176781"
---
# <a name="messages-element-xmla"></a>Элемент Messages (XML для аналитики)
  Содержит коллекцию элементов [Message](message-element-xmla.md) , возвращаемую экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] при вызове метода [Discover](../xml-elements-methods-discover.md) или [Execute](../xml-elements-methods-execute.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
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
|Родительские элементы|[Результирующий набор](../xml-data-types/resultset-data-type-xmla.md)|  
|Дочерние элементы|[Сообщение](message-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент используется в случаях, когда вызов метода `Discover` или отдельная команда XMLA в вызове метода `Execute` завершается успешно, но с ошибками или предупреждениями. В таких случаях `Messages` добавляется элемент [корневой](root-element-xmla.md) элемент после всех остальных элементов, который в свою очередь содержит один или несколько `Message` элементов. Каждый `Message` элемент представляет одно сообщение, ошибку или предупреждение, которое возвращается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
