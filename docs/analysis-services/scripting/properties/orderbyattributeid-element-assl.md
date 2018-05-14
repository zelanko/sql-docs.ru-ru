---
title: Элемент OrderByAttributeID (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e6ab7a00961d4e5b925556d107eec32b7ddb9c9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
## <a name="remarks"></a>Примечания  
 **OrderByAttributeID** элемент используется, только если значение [OrderBy](../../../analysis-services/scripting/properties/orderby-element-assl.md) элемент для **DimensionAttribute** равно *AttributeKey* или *AttributeName*.  
  
 Элемент, соответствующий родителю параметра **OrderByAttributeID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
