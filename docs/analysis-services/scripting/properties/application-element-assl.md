---
title: "Элемент Application (ASSL) | Документы Microsoft"
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
apiname: Application Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Application
helpviewer_keywords: Application element
ms.assetid: dfd780ad-f643-4a1c-b58b-34271ae91240
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ce8773397787599ed8f0df041eea0f683b309d58
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="application-element-assl"></a>Элемент Application (ASSL)
  Определяет приложение, связанное с [действия](../../../analysis-services/scripting/objects/action-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   ...  
   <Application>...</Application>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md) или один из его производных элементов: [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md), [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **Application** может использоваться клиентскими приложениями для определения действий, применимых к конкретному клиентскому приложению. Клиентское приложение отвечает за проверку значения этого элемента.  
  
 Элемент, соответствующий родителю параметра **приложения** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Actions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
