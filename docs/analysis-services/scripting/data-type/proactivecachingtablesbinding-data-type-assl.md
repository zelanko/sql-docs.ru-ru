---
title: "Тип данных ProactiveCachingTablesBinding (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ProactiveCachingTablesBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: ProactiveCachingTablesBinding data type
ms.assetid: f6b3f6fc-757c-4b1e-bb3a-d26482888d14
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ed3dd65913b659f0c04c684be93ea3850940a1cb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="proactivecachingtablesbinding-data-type-assl"></a>Тип данных ProactiveCachingTablesBinding (ASSL)
  Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) об изменениях источника данных в указанных таблицах и представлениях, требующих перестройки кэша.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <!-- The following elements extend ProactiveCachingObjectNotificationBinding -->  
   <TableNotification>...</TableNotification>  
</ProactiveCachingTablesBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[ProactiveCachingObjectNotificationBinding](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **ProactiveCachingBinding** типа, включая таблицу иерархии наследования **ProactiveCachingBinding** типов, в разделе [данных ProactiveCachingBinding Введите &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) **привязки** тип и иерархию наследования **привязки**  типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ProactiveCachingTablesBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
