---
title: Элемент TableID (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5fb772f2d4dc003897d359e67f6d3b185cc506a6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tableid-element-assl"></a>Элемент TableID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит идентификатор (ID) таблицы (из [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md) элемент) связанный с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ColumnBinding> <!-- or DSVTableBinding, RowBinding, IncrementalProcessingNotification -->  
   ...  
   <TableID>...</TableID>  
   ...  
</ColumnBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [DSVTableBinding](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md), [IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md), [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Таблица, идентифицируемая **TableID** должно быть в пределах источника данных, к которому привязан объект-владелец (измерение или куб).  
  
 Элементы, соответствующие родителям элемента **TableID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ColumnBinding>, <xref:Microsoft.AnalysisServices.DSVTableBinding>, <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>, и <xref:Microsoft.AnalysisServices.RowBinding>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
