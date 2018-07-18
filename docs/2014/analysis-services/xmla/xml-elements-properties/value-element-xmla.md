---
title: Значение элемента (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8defb7fe2115bd1ea9ccb7b3f23b0717db8b9aef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263256"
---
# <a name="value-element-xmla"></a>Value, элемент (XML для аналитики)
  Содержит необходимое значение параметра [атрибут](attribute-element-xmla.md) элемент могут добавить [вставить](../xml-elements-commands/insert-element-xmla.md) команды, или [ячейки](cell-element-xmla.md) элемента должны обновляться с [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)команды.  
  
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
|Родительские элементы|[Атрибут](attribute-element-xmla.md), [ячейки](cell-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элемента `Attribute` элемент `Value` содержит нужное значение, которое должен содержать элемент после фиксации команды `Insert`. Дополнительные сведения о вставке элементов см. в разделе [Вставка, обновление и удаление членов &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Для элемента `Cell` элемент `Value` содержит нужное значение, которое должна содержать ячейка после фиксации команды `UpdateCells`. Фактическое значение, хранящееся в таблице обратной записи для этой ячейки, представляет собой разность исходного значения ячейки и ее нужного значения.  
  
 Тип данных этого элемента должен совпадать с типом данных обновляемой ячейки.  
  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент CellOrdinal &#40;XML для Аналитики&#41;](cellordinal-element-xmla.md)   
 [Вставка элемента &#40;XML для Аналитики&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Элемент UpdateCells &#40;XML для Аналитики&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
