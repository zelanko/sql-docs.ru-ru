---
title: Элемент Algorithm (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Algorithm Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9fb2ab30f6abd753f0c954ef41ad26d0af9dcda8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149784"
---
# <a name="algorithm-element-assl"></a>Элемент Algorithm (ASSL)
  Определяет алгоритм, используемый в [MiningModel](../objects/miningmodel-element-assl.md) элемент.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением элемента `Algorithm` является строка, которая идентифицирует алгоритм. Например, эта строка может иметь *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, или *Microsoft_Clustering.* Строка идентифицирует алгоритмы, предоставляемые [!INCLUDE[msCoName](../../../includes/msconame-md.md)] и пользовательские алгоритмы, предоставленные пользователем. Доступные значения для `Algorithm` элемента можно получить из столбца SERVICE_NAME [DMSCHEMA_MINING_SERVICES](../../schema-rowsets/data-mining/dmschema-mining-services-rowset.md) набора строк схемы.  
  
 Элемент, соответствующий родителю параметра `Algorithm` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MiningModel>. Тесно связанным элементом в модели объектов AMO является <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AlgorithmParameter &#40;ASSL&#41;](../objects/algorithmparameter-element-assl.md)   
 [Элемент AlgorithmParameters &#40;ASSL&#41;](../collections/algorithmparameters-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
