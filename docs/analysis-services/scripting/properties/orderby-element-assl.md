---
title: "Элемент OrderBy (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: OrderBy Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: OrderBy
helpviewer_keywords: OrderBy element
ms.assetid: d7a0564b-430e-44eb-913a-fe1f98917d0f
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8fcd65d4c4015a79435404bd9c3fc74e6e04139d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="orderby-element-assl"></a>Элемент OrderBy (ASSL)
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
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
