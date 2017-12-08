---
title: "Ячейки элемент (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Cell Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords: Cell element
ms.assetid: 88daba54-89e9-423f-8d12-8de80cf52d6b
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b6a57a3c7da9418dafb1899fddebc2d5646adf81
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cell-element-xmla"></a>Элемент Cell (XML для аналитики)
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
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
