---
title: "Тип данных ProactiveCachingIncrementalProcessingBinding (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ProactiveCachingIncrementalProcessingBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ProactiveCachingIncrementalProcessingBinding data type
ms.assetid: f49c0c96-4277-417b-9660-d77a4faebd00
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 593a10991ea472897e1c5744614f82f0410467d5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="proactivecachingincrementalprocessingbinding-data-type-assl"></a>Тип данных ProactiveCachingIncrementalProcessingBinding (ASSL)
  Определяет производный тип данных, представляющий привязку к [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о состоянии процесса перестройки кэша.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingIncrementalProcessingBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</ RefreshInterval >  
   <IncrementalProcessingNotification>...</ IncrementalProcessingNotification >  
</ProactiveCachingIncrementalProcessingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md), [RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md)|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **ProactiveCachingBinding** типа, включая таблицу иерархии наследования **ProactiveCachingBinding** типов, в разделе [данных ProactiveCachingBinding Введите &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) **привязки** тип и иерархию наследования **привязки**  типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
