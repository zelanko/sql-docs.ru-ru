---
title: Где элемент (XMLA) | Документы Microsoft
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
- Where Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Where
- microsoft.xml.analysis.where
- http://schemas.microsoft.com/analysisservices/2003/engine#Where
helpviewer_keywords:
- Where element
ms.assetid: 81fb4190-3379-4ddf-8795-a0772f3b92bb
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4e63d2ecd6f20d374c6746c7d3bc77ad455f1ef6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195019"
---
# <a name="where-element-xmla"></a>Элемент Where (XML для аналитики)
  Определяет условие фильтра, используемое родительской командой [Drop](../xml-elements-commands/drop-element-xmla.md) или [Update](../xml-elements-commands/update-element-xmla.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Drop> <!-- or Update -->  
   ...  
   <Where>  
      <Attributes>...</Attributes>  
   </Where>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Drop](../xml-elements-commands/drop-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md)|  
|Дочерние элементы|[Атрибуты](attributes-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для `Drop` команд, `Where` элемента, в сочетании с [DeleteWithDescendants](deletewithdescendants-element-xmla.md) определяет область элементов атрибута для удаления.  
  
 Для команд `Update` элемент `Where` определяет область элементов атрибута, подлежащих обновлению. С помощью сочетания атрибутов, включенных в коллекцию `Attributes` родительской команды `Update` и в коллекцию `Attributes` элемента `Where`, возможно обновление нескольких элементов атрибута.  
  
 Дополнительные сведения об удалении и обновлении элементов атрибутов см. в разделе [Вставка, обновление и удаление элементов (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  