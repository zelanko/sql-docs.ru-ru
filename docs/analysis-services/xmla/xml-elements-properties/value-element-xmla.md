---
title: "Значение элемента (XMLA) | Документы Microsoft"
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
- Value Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61a5fa276918a176eb60340fce44e5dfdae0d4da
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-xmla"></a>Value, элемент (XML для аналитики)
  Содержит необходимое значение параметра [атрибута](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) элемента, который требуется добавить, [вставить](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) команды, или [ячейки](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) элемент будет обновлен [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Любой|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибут](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [ячейки](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Для **атрибута** элементов, **значение** элемент содержит нужное значение, которое должен содержать элемент после **вставить** команда фиксируется. Дополнительные сведения о вставке элементов см. в разделе [Вставка, обновление и удаление элементов &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Для **ячейки** элементов, **значение** элемент содержит нужное значение, которое должна содержать ячейка после **UpdateCells** команда фиксируется. Фактическое значение, хранящееся в таблице обратной записи для этой ячейки, представляет собой разность исходного значения ячейки и ее нужного значения.  
  
 Тип данных этого элемента должен совпадать с типом данных обновляемой ячейки.  
  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Элемент CellOrdinal &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [Вставить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент UpdateCells &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

