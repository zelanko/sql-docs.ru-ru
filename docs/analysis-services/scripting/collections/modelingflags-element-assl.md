---
title: "Элемент ModelingFlags (ASSL) | Документы Microsoft"
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
apiname: ModelingFlags Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ModelingFlags
helpviewer_keywords: ModelingFlags element
ms.assetid: 83968c1e-aae8-4657-aa53-d971de0dc834
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 60a85d1f6b7b079ab3ea09148299c9edc1f155f3
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="modelingflags-element-assl"></a>Элемент ModelingFlags (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит коллекцию элементов [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) для столбца в [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) или [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelColumn> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <ModelingFlags>  
      <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
   </ModelingFlags>  
   ...  
</MiningModelColumn>  
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
|Родительские элементы|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
