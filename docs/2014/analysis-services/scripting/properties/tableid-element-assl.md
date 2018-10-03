---
title: Элемент TableID (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TableID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableID
helpviewer_keywords:
- TableID element
ms.assetid: 45fe7e23-b274-4bc2-be63-1a5bb6680f51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7fd2304c4f442102ff8d654bec3be19e34bdd944
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201584"
---
# <a name="tableid-element-assl"></a>Элемент TableID (ASSL)
  Содержит идентификатор (ID) таблицы (из [DataSourceView](../objects/datasourceview-element-assl.md) элемент) связанных с родительским элементом.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ColumnBinding](../data-type/binding-data-type-assl.md), [DSVTableBinding](../data-type/tablebinding-data-type-assl.md), [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md), [RowBinding](../data-type/rowbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Таблица, указанная элементом `TableID`, должна находиться в источнике данных, к которому привязан объект-владелец (измерение или куб).  
  
 Элементы, соответствующие родителям элемента `TableID` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ColumnBinding>, <xref:Microsoft.AnalysisServices.DSVTableBinding>, <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification> и <xref:Microsoft.AnalysisServices.RowBinding>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
