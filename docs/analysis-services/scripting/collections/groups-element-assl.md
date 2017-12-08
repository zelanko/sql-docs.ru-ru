---
title: "Группирует элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: Groups Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Groups
helpviewer_keywords: Groups element
ms.assetid: 62196435-83a8-4a0a-8be1-7dfc986dc6c5
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a131f96b8c3c01c8103408fc85d97b2903fbafe7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="groups-element-assl"></a>Элемент Groups (ASSL)
  Содержит коллекцию групп элементов, привязанных к атрибуту.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Binding xsi:type="UserDefinedGroupBinding">  
   ...  
   <Groups>  
      <Group>...</Group>  
   </Groups>  
   ...  
</Binding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Привязка](../../../analysis-services/scripting/data-type/binding-data-type-assl.md) типа [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|Дочерние элементы|[Группирование](../../../analysis-services/scripting/objects/group-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.GroupCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Источники данных и привязки &#40; Многомерные службы SSAS &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
