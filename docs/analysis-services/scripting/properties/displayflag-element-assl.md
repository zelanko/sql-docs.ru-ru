---
title: "Элемент DisplayFlag (ASSL) | Документы Microsoft"
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
- DisplayFlag Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DisplayFlag
helpviewer_keywords:
- DisplayFlag element
ms.assetid: a6750477-0763-46da-9add-1f4448146a6b
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a28934e2249a9fe1b16ebffb8e19dea4fed34501
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="displayflag-element-assl"></a>Элемент DisplayFlag (ASSL)
  Содержит подсказку только для чтения, которая указывает, должны ли компоненты пользовательского интерфейса Показывать связанный [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ServerProperty>  
   ...  
   <DisplayFlag>...</DisplayFlag>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родительский **DisplayFlag** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент ServerProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)   
 [Элемент Server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

