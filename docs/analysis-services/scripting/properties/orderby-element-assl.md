---
title: Элемент OrderBy (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ac17b52d36b414854da027dc3cf2c4a8f768e9f6
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
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
  
  
