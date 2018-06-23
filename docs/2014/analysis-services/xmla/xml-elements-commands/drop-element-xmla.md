---
title: Удалить элемент (XMLA) | Документы Microsoft
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
- Drop Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Drop
- microsoft.xml.analysis.drop
- http://schemas.microsoft.com/analysisservices/2003/engine#Drop
helpviewer_keywords:
- Drop element
ms.assetid: a5d21db3-743a-4958-b16d-b6816a5ee787
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64f6fd75c3c5032c035ca4af6b9950a0de1e6ddc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194336"
---
# <a name="drop-element-xmla"></a>Элемент Drop (XML для аналитики)
  Удаляет элементы атрибута из измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Drop>  
      <Object>...</Object>  
      <DeleteWithDescendants>...</DeleteWithDescendants>  
      <Where>...</Where>  
   </Drop>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[DeleteWithDescendants](../xml-elements-properties/deletewithdescendants-element-xmla.md), [объекта](../xml-elements-properties/object-element-dimension-xmla.md), [где](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `Drop` удаляет элементы атрибутов из измерения, доступного для записи.  
  
 Дополнительные сведения об удалении элементов см. в разделе [Вставка, обновление и удаление членов &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент INSERT &#40;XML для Аналитики&#41;](insert-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](update-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  