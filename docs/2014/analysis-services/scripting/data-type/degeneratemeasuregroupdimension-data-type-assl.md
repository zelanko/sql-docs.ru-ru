---
title: Тип данных DegenerateMeasureGroupDimension (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DegenerateMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DegenerateMeasureGroupDimension
helpviewer_keywords:
- DegenerateMeasureGroupDimension data type
ms.assetid: a64fe908-154d-4fea-b435-afb6ee37a6fa
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 343668137e77f53f94df2b6bc1324c3a67d94256
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321161"
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
|Базовые типы данных|[RegularMeasureGroupDimension](dimension-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об измерениях фактов см. в разделе [связей измерений](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DegenerateMeasureGroupDimension>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
