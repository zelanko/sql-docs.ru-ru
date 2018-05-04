---
title: Элемент OrderByAttributeID (ASSL) | Документы Microsoft
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
- OrderByAttributeID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- OrderByAttributeID
helpviewer_keywords:
- OrderByAttributeID element
ms.assetid: 41d7b650-ac40-4f1a-850d-2f81a19b28cb
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9d630aa03e0080b2dabac7b53e51f90f2a3c6694
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="orderbyattributeid-element-assl"></a>Элемент OrderByAttributeID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет другой атрибут, по которому выполняется упорядочивание элементов атрибута [измерения](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderByAttributeID>...</OrderByAttributeID>  
   ...  
</DimensionAttribute>  
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
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **OrderByAttributeID** элемент используется, только если значение [OrderBy](../../../analysis-services/scripting/properties/orderby-element-assl.md) элемент для **DimensionAttribute** равно *AttributeKey* или *AttributeName*.  
  
 Элемент, соответствующий родителю параметра **OrderByAttributeID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
