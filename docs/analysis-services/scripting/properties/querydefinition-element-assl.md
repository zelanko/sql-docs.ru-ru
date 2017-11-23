---
title: "Элемент QueryDefinition (ASSL) | Документы Microsoft"
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
apiname: QueryDefinition Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: QueryDefinition
helpviewer_keywords: QueryDefinition element
ms.assetid: 25bf0e93-d5c5-41df-b310-a253a4ace80e
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 35f71810388221724cd364ffadcab6f14f0be655
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="querydefinition-element-assl"></a>Элемент QueryDefinition (ASSL)
  Содержит непрозрачное выражение для запроса, связанного с [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) элемент в [QueryBinding](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<QueryBinding>  
   ...  
   <QueryDefinition>...</QueryDefinition>  
   ...  
</QueryBinding>  
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
|Родительский элемент|[QueryBinding](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **QueryDefinition** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.QueryBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
