---
title: Тип данных ProactiveCachingBinding (ASSL) | Документы Microsoft
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
- ProactiveCachingBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6311850e1373c3731c26bba7eeee0eb6ef0498d9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="proactivecachingbinding-data-type-assl"></a>Тип данных ProactiveCachingBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет абстрактный производный тип данных, представляющий сведения для [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) сведения об изменениях источника данных, которые требуют перестройки кэша, или о состоянии процесса перестройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Производные типы данных|[ProactiveCachingIncrementalProcessingBinding](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md), [ProactiveCachingObjectNotificationBinding](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md), [ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Remarks  
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
  
  
