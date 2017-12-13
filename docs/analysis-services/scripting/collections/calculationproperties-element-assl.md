---
title: "Элемент CalculationProperties (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CalculationProperties Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CalculationProperties
helpviewer_keywords: CalculationProperties element
ms.assetid: dccfe036-0b1b-4877-8bdd-4b128ccb55c9
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a53b11f83a0ab5103ac27e9b2a33ae277b8d9ef6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="calculationproperties-element-assl"></a>Элемент CalculationProperties (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит коллекцию элементов [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) элементы, связанные с [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MdxScript>  
   ...  
   <CalculationProperties>  
      <CalculationProperty>...</CalculationProperty>  
   </CalculationProperties>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|  
|Дочерние элементы|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.CalculationPropertyCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
