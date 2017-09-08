---
title: "Элемент Visibility (ASSL) | Документы Microsoft"
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
- Visibility Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Visibility
helpviewer_keywords:
- Visibility element
ms.assetid: 59372ebf-af52-4d60-bf9b-bb1644ae9865
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61335ffb9e3816d67f89c21b42a5da9ffa88e6f0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="visibility-element-assl"></a>Элемент Visibility (ASSL)
  Определяет видимость элемента [заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Annotation>  
   ...  
   <Visibility>...</Visibility>  
   ...  
</Annotation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*SchemaRowset*|Заметки в наборе строк схемы видны.|  
|*None*|Заметки не видны.|  
  
 Перечисление, соответствующее разрешенным значениям для **видимость** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
