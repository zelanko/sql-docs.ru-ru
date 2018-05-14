---
title: Элемент OrderBy (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2d2c8caf392e5d80d82b06a7d7fd9b5cd724a35e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="orderby-element-assl"></a>Элемент OrderBy (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает, как упорядочивать элементы, содержащиеся в атрибуте.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Название*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Название*|Упорядочить по имени элемента.|  
|*Key*|Упорядочить по ключу элемента.|  
|*AttributeKey*|Упорядочить по ключу элемента атрибута, заданного в [OrderByAttributeID](../../../analysis-services/scripting/properties/orderbyattributeid-element-assl.md) элемент **DimensionAttribute**.|  
|*AttributeName*|Упорядочить по имени элемента атрибута, заданного в элементе **OrderByAttributeID** для **DimensionAttribute**.|  
  
 Перечисление, соответствующее разрешенным значениям для **OrderBy** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.OrderBy>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
