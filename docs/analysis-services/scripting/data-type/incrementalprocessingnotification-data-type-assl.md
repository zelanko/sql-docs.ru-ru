---
title: Тип данных IncrementalProcessingNotification (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IncrementalProcessingNotification Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- IncrementalProcessingNotification data type
ms.assetid: 66e27f92-65c1-4a34-b9c2-bfbb5aeb7d7c
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5dbb159d2de320bc5fb9fdc8188488e2429d81b2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="incrementalprocessingnotification-data-type-assl"></a>Тип данных IncrementalProcessingNotification (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий для элемента [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) сведения о предназначенном для выполнения запросе с целью определения процесса добавочной обработки.  
  
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
|Производные элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ProactiveCachingQueryBinding & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
