---
title: "Элемент Algorithm (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Algorithm Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fe1a9caffdff1de0dc62c4ddd696e1ec8b829bd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="algorithm-element-assl"></a>Элемент Algorithm (ASSL)
  Определяет алгоритм, используемый [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение **алгоритм** элемент представляет собой строку, которая идентифицирует алгоритм. Например, эта строка может иметь *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, или *Microsoft_Clustering.* Строка идентифицирует алгоритмы, предоставляемые [!INCLUDE[msCoName](../../../includes/msconame-md.md)] и пользовательские алгоритмы, предоставленные пользователем. Доступные значения для **алгоритм** элемента можно получить из столбца SERVICE_NAME [DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) набора строк схемы.  
  
 Элемент, соответствующий родителю параметра **алгоритм** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningModel>. Тесно связанным элементом в модели объектов AMO является <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент AlgorithmParameter &#40; ASSL &#41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)   
 [Элемент AlgorithmParameters &#40; ASSL &#41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
