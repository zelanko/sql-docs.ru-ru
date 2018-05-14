---
title: Ячейки элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 014f46219ece054c292ff3a3b7a11d98c07c1547
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="cell-element-xmla"></a>Элемент Cell (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит сведения о ячейке, которая будет обновлена командой [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<UpdateCells>  
   ...  
   <Cell CellOrdinal="Long">  
      <Value>...</Value>  
   </Cell>  
   ...  
</UpdateCells>  
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
|Родительские элементы|[UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Дочерние элементы|[Значение](../../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|CellOrdinal|Обязательный атрибут типа **Long** . Содержит отсчитываемый от нуля порядковый номер ячейки, которая будет обновлена.|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
