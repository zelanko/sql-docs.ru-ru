---
title: "Элемент CellOrdinal (XML для Аналитики) | Документы Microsoft"
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
apiname: CellOrdinal Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cellordinal
- urn:schemas-microsoft-com:xml-analysis#CellOrdinal
- http://schemas.microsoft.com/analysisservices/2003/engine#CellOrdinal
helpviewer_keywords: CellOrdinal element
ms.assetid: 1808c498-e3b4-4e5c-9e22-7f8662d32874
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d4fee3f8cfb4bc664734944316c4fcb9996d2a2c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cellordinal-element-xmla"></a>Элемент CellOrdinal (XML для аналитики)
  Содержит порядковый номер в кубе ячейки будет обновлен [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cell>  
   ...  
   <CellOrdinal>...</CellOrdinal>  
   ...  
</Cell>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Long|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Ячейки](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **CellOrdinal** элементов определяет ячейку, будет обновлен **UpdateCells** команды.  
  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Значение элемента &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md)   
 [Элемент UpdateCells &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
