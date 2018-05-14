---
title: Элемент ColumnID (EventColumn) (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e60f8ada3852bdbd09c8f7831b4af0110bb6a630
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="columnid-element-eventcolumn-assl"></a>Элемент ColumnID (EventColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит идентификатор (ID) столбца с данными, которые будут захвачены для события как часть [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[EventColumn](../../../analysis-services/scripting/data-type/eventcolumn-data-type-assl.md)|  
|Дочерние элементы|Нет.|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра **ColumnID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.TraceColumn>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Columns &#40;ASSL&#41;](../../../analysis-services/scripting/collections/columns-element-assl.md)   
 [Элемент Event &#40;ASSL&#41;](../../../analysis-services/scripting/objects/event-element-assl.md)   
 [Элемент Events &#40;ASSL&#41;](../../../analysis-services/scripting/collections/events-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
