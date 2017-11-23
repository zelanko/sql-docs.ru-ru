---
title: "Элемент Members (ASSL) | Документы Microsoft"
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
apiname: Members Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Members
helpviewer_keywords: Members element
ms.assetid: 4bf585a3-b681-486d-852b-1244c5658a04
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8b7a4a67e738d500661a430a1fb55a93284c50e8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="members-element-assl"></a>Элемент Members (ASSL)
  Содержит коллекцию элементов [Member](../../../analysis-services/scripting/objects/member-element-assl.md) для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Group> <!-- or Role --<  
   ...  
   <Members>  
      <Member>...</Member>  
   </Members>  
   ...  
</Group>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Group](../../../analysis-services/scripting/objects/group-element-assl.md), [Role](../../../analysis-services/scripting/objects/role-element-assl.md)|  
|Дочерние элементы|[Член](../../../analysis-services/scripting/objects/member-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Элементы, соответствующие родителям элемента **элементы** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Group> и <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
