---
title: "Элемент AlgorithmParameter (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: AlgorithmParameter Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AlgorithmParameter
helpviewer_keywords: AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 73fd9b4b96ea774eaf352bddf7bab1fb143f1bf4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="algorithmparameter-element-assl"></a>Элемент AlgorithmParameter (ASSL)
  Определяет параметр для алгоритма, используемого в [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0–n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AlgorithmParameters](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|  
|Дочерние элементы|[Name](../../../analysis-services/scripting/properties/name-element-assl.md), [Value](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 **AlgorithmParameter** — это параметр для алгоритма модели интеллектуального анализа данных. Элемент **AlgorithmParameter** представляет этот параметр в виде пары имя-значение. Набор применимых параметров, которые может представить элемент **AlgorithmParameter** , зависит от алгоритма. Дополнительные сведения о параметрах конкретного алгоритма см. в соответствующей документации по этому алгоритму.  
  
 Доступные параметры алгоритма, включая сведения о проверке и отображения, могут быть получены из [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) набора строк схемы.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент MiningModel &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Элемент Algorithm &#40; ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
