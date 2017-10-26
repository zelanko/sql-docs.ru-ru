---
title: "Элемент UpdateCells (XML для Аналитики) | Документы Microsoft"
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
- UpdateCells Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.updatecells
- urn:schemas-microsoft-com:xml-analysis#UpdateCells
- http://schemas.microsoft.com/analysisservices/2003/engine#UpdateCells
helpviewer_keywords:
- UpdateCells command
ms.assetid: 18336a35-8a46-4532-9ee7-71828b2982af
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21e635489871f841a85f40db2bd333ceec2205ea
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="updatecells-element-xmla"></a>Элемент UpdateCells (XML для аналитики)
  Обновляет ячейки в кубе, доступном для записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <UpdateCells>  
      <Cell>...</Cell>  
   </UpdateCells>  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Ячейки](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Команда **UpdateCells** обновляет ячейки в кубе, которые поддерживают обратную запись в ячейки.  
  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Удалить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Вставить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Обновить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

