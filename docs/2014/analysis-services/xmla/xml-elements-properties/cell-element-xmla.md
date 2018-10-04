---
title: Ячейки элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cell Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: 88daba54-89e9-423f-8d12-8de80cf52d6b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec8b6eee3e3eefe1c86bf92d45bfac6032905f8e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219414"
---
# <a name="cell-element-xmla"></a>Элемент Cell (XML для аналитики)
  Содержит сведения о ячейке, которая будет обновлена командой [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md) .  
  
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
|Родительские элементы|[UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)|  
|Дочерние элементы|[Value](value-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|CellOrdinal|Требуется `Long` атрибута. Содержит отсчитываемый от нуля порядковый номер ячейки, которая будет обновлена.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
