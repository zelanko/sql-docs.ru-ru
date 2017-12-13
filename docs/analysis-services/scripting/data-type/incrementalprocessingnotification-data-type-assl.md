---
title: "Тип данных IncrementalProcessingNotification (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IncrementalProcessingNotification Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: IncrementalProcessingNotification data type
ms.assetid: 66e27f92-65c1-4a34-b9c2-bfbb5aeb7d7c
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 52e12cccdaba40a69a8f73e22c0cbe4f979d7d56
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="incrementalprocessingnotification-data-type-assl"></a>Тип данных IncrementalProcessingNotification (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросе, следует выполнить для определения хода выполнения добавочной обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<IncrementalProcessingNotification>  
   <!-- The following elements extend QueryNotification -->  
   <TableID>...</TableID>  
   <ProcessingQuery>...</ProcessingQuery>  
</IncrementalProcessingNotification>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[ProcessingQuery](../../../analysis-services/scripting/properties/processingquery-element-assl.md), [TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md)|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных ProactiveCachingQueryBinding &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
