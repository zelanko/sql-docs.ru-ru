---
title: Элемент Algorithm (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d60c8416ef530014ee996f57b321f46ffbb2e436
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="algorithm-element-assl"></a>Элемент Algorithm (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Значение **алгоритм** элемент представляет собой строку, которая идентифицирует алгоритм. Например, эта строка может иметь *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, или *Microsoft_Clustering.* Строка идентифицирует алгоритмы, предоставляемые [!INCLUDE[msCoName](../../../includes/msconame-md.md)] и пользовательские алгоритмы, предоставленные пользователем. Доступные значения для **алгоритм** элемента можно получить из столбца SERVICE_NAME [DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) набора строк схемы.  
  
 Элемент, соответствующий родителю параметра **алгоритм** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningModel>. Тесно связанным элементом в модели объектов AMO является <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AlgorithmParameter & #40; ASSL & #41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)   
 [Элемент AlgorithmParameters & #40; ASSL & #41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
