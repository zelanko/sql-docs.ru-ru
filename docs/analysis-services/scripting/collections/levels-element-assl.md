---
title: "Уровни элемент (ASSL) | Документы Microsoft"
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
apiname: Levels Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Levels
helpviewer_keywords: Levels element
ms.assetid: a9dd4890-a5da-48e7-9bbf-f857107cde8d
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3e4f18891235bb4336868d4efa135805a15a2ccd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="levels-element-assl"></a>Элемент Levels (ASSL)
  Содержит коллекцию элементов [уровень](../../../analysis-services/scripting/objects/level-element-assl.md) элементов в [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Hierarchy>  
      ...  
   <Levels>  
      <Level>...</Level>  
   </Levels>  
   ...  
</Hierarchy>  
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
|Родительские элементы|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
|Дочерние элементы|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.LevelCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
