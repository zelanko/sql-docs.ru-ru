---
title: Элемент MembersWithData (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MembersWithData Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6826e7e64e2f4562527b6af9189426d205d5037
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="memberswithdata-element-assl"></a>Элемент MembersWithData (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, следует ли отображать элементы данных для неконечных элементов в родительском атрибуте.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*NonLeafDataVisible*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение **MembersWithData** элемент используется только родительскими атрибутами (другими словами, значение [использование](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) элемент **DimensionAttribute** родительского элемента имеет значение *родительского*) чтобы определить, следует ли отображать элементы данных для неконечных элементов в родительском атрибуте. Дополнительные сведения об элементах данных см. в разделе [Атрибуты в иерархиях типа "родители-потомки"](../../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md).  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*NonLeafDataHidden*|Неконечные данные скрыты.|  
|*NonLeafDataVisible*|Неконечные данные видимы.|  
  
 Перечисление, соответствующее разрешенным значениям для **MembersWithData** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MembersWithDataCaption &#40;ASSL&#41;](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)   
 [Тип данных DimensionAttribute &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
