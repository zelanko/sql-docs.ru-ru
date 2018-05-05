---
title: Тип данных AggregationInstanceCubeDimension (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregationInstanceCubeDimension Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AggregationInstanceCubeDimension data type
ms.assetid: b321ad9e-f034-4a7b-b0b7-8ba5fb162e7e
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3e93ae8ed7f727c6ca6c1f56b47b381b45eb3742
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationinstancecubedimension-data-type-assl"></a>Тип данных AggregationInstanceCubeDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет примитивный тип данных, представляющий сведения об измерении куба, которое используется экземпляром агрегата.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationInstanceCubeDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <KeyColumns>...</KeyColumns>  
   <Attributes>...</Attributes>  
</AggregationInstanceCubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md), [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|Производные элементы|[Измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
