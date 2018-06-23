---
title: Элемент ColumnID (EventColumn) (ASSL) | Документы Microsoft
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
- ColumnID Element (EventColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnID
helpviewer_keywords:
- ColumnID element
ms.assetid: c4f4fbad-9d70-4de2-8cf7-caee80a4a1e4
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 71e51ec736b10a6d72621efb2a9b094882ed8057
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193884"
---
# <a name="columnid-element-eventcolumn-assl"></a>Элемент ColumnID (EventColumn) (ASSL)
  Содержит идентификатор (ID) столбца с данными, которые будут захвачены для события как часть [трассировки](../objects/trace-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[EventColumn](../data-type/eventcolumn-data-type-assl.md)|  
|Дочерние элементы|Нет.|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ColumnID` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.TraceColumn>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Columns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Элемент Event &#40;ASSL&#41;](../objects/event-element-assl.md)   
 [Элемент Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  