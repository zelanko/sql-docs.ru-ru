---
title: "Тип данных DegenerateMeasureGroupDimension (ASSL) | Документы Microsoft"
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
- DegenerateMeasureGroupDimension Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DegenerateMeasureGroupDimension
helpviewer_keywords:
- DegenerateMeasureGroupDimension data type
ms.assetid: a64fe908-154d-4fea-b435-afb6ee37a6fa
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b40aa4385a78f54e4c01b637849678777036ee66
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="degeneratemeasuregroupdimension-data-type-assl"></a>Тип данных DegenerateMeasureGroupDimension (ASSL)
  Определяет производный тип данных, представляющий связь между вырожденным измерением (то есть измерением фактов) и группой мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DegenerateMeasureGroupDimension>  
   <!-- DegenerateMeasureGroupDimension does not have any elements that extend RegularMeasureGroupDimension -->  
</DegenerateMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения об измерениях фактов см. в разделе [связей измерений](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DegenerateMeasureGroupDimension>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

