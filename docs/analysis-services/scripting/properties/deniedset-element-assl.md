---
title: "Элемент DeniedSet (ASSL) | Документы Microsoft"
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
- DeniedSet Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DeniedSet
helpviewer_keywords:
- DeniedSet element
ms.assetid: 898deefb-822d-458b-96d8-880da287b687
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71eda4e182bf13f61df813e9297bbd12c69192fd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deniedset-element-assl"></a>Элемент DeniedSet (ASSL)
  Содержит выражение набора, определяющее список разрешений, которые отклоняются для связанного атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributePermission>  
      ...  
   <DeniedSet>...</DeniedSet>  
      ...  
</AttributePermission>  
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
|Родительский элемент|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **DeniedSet** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

