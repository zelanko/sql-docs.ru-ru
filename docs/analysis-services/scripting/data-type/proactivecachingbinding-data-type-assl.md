---
title: "Тип данных ProactiveCachingBinding (ASSL) | Документы Microsoft"
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
apiname: ProactiveCachingBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cb1f1d86b26222e327fc36090113cb4a0d5ce4ad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="proactivecachingbinding-data-type-assl"></a>Тип данных ProactiveCachingBinding (ASSL)
  Определяет абстрактный производный тип данных, представляющий сведения для [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) сведения об изменениях источника данных, которые требуют перестройки кэша, или о состоянии процесса перестройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Производные типы данных|[ProactiveCachingIncrementalProcessingBinding](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md), [ProactiveCachingObjectNotificationBinding](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md), [ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) **привязки** тип и иерархию наследования **привязки**  типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
## <a name="inheritance-hierarchy-of-proactivecachingbinding-types"></a>Иерархия наследования типов данных ProactiveCachingBinding  
 Следующая иерархия показывает наследование типов данных **ProactiveCachingBinding** .  
  
 [Привязка](../../../analysis-services/scripting/data-type/binding-data-type-assl.md) элемент  
  
 Элемент**ProactiveCachingBinding**   
  
 [ProactiveCachingObjectNotificationBinding](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md) элемент  
  
 [ProactiveCachingInheritedBinding](../../../analysis-services/scripting/data-type/proactivecachinginheritedbinding-data-type-assl.md) элемент  
  
 [ProactiveCachingTablesBinding](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md) элемент  
  
 [ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md) элемент  
  
 [ProactiveCachingIncrementalProcessingBinding](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md) элемент  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
