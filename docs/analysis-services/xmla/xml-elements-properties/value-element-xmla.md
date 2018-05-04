---
title: Значение элемента (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: 18e6190fabc53df42e7ebd1d7284dfd3f987fbfe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="value-element-xmla"></a>Value, элемент (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 Для **атрибута** элементов, **значение** элемент содержит нужное значение, которое должен содержать элемент после **вставить** команда фиксируется. Дополнительные сведения о вставке элементов см. в разделе [Вставка, обновление и удаление членов &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Для **ячейки** элементов, **значение** элемент содержит нужное значение, которое должна содержать ячейка после **UpdateCells** команда фиксируется. Фактическое значение, хранящееся в таблице обратной записи для этой ячейки, представляет собой разность исходного значения ячейки и ее нужного значения.  
  
 Тип данных этого элемента должен совпадать с типом данных обновляемой ячейки.  
  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент CellOrdinal &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [Вставить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент UpdateCells & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
