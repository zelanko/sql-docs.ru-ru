---
title: Сообщения элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 90579f9204a263b4b2366e4b1eeab714676a4be7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="messages-element-xmla"></a>Элемент Messages (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию элементов [Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md) , возвращаемую экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] при вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Результирующий набор](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Дочерние элементы|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент используется в случаях, когда вызов метода **Discover** или отдельная команда XMLA в вызове метода **Execute** завершается успешно, но с ошибками или предупреждениями. В таких случаях элемент **Messages** добавляется в элемент [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) после всех остальных элементов, содержащих один или несколько элементов **Message** . Каждый элемент **Message** представляет одно сообщение (ошибку или предупреждение), которое возвращается экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
