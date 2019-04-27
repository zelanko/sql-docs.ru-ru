---
title: Свойства интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80e7a793973ddbe0e55862d2e68f23e6c7e31dc3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746836"
---
# <a name="data-mining-properties"></a>Свойства интеллектуального анализа данных
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера интеллектуального анализа данных, перечисленные в следующих таблицах. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Применимо к:** Только многомерный режим сервера  
  
## <a name="non-specific-category"></a>Общая категория  
 `AllowSessionMiningModels`  
 Логическое свойство, указывающее, можно ли создать модели интеллектуального анализа данных в сеансах.  
  
 Значение этого свойства по умолчанию равно false, что указывает, что модели интеллектуального анализа данных в сеансах создавать нельзя.  
  
 `AllowAdHocOpenRowsetQueries`  
 Логическое свойство, указывающее, разрешены ли специализированные запросы открытых наборов строк.  
  
 Значение этого свойства по умолчанию равно false, что указывает, что запросы открытых наборов строк не разрешены во время сеанса.  
  
 `AllowedProvidersInOpenRowset`  
 Строковое свойство, идентифицирующее, какие поставщики разрешены в открытом наборе строк, состоящее из списка идентификаторов поставщиков ProgID, разделенного запятыми/точками с запятыми, или из строки «[All]».  
  
 `MaxConcurrentPredictionQueries`  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее максимальное количество параллельных прогнозирующих запросов.  
  
## <a name="algorithms-category"></a>Категория алгоритмов  
 `Microsoft_Association_Rules\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Association_Rules.  
  
 `Microsoft_Clustering\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Clustering.  
  
 `Microsoft_Decision_Trees\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_DecisionTrees.  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Naive_Bayes.  
  
 `Microsoft_Neural_Network\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Neural_Network.  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Sequence_Clustering.  
  
 `Microsoft_Time_Series\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Time_Series.  
  
 `Microsoft_Linear_Regression\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Linear_Regression.  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Logistic_Regression.  
  
> [!NOTE]  
>  В дополнение к свойствам, которые определяют доступные службы интеллектуального анализа данных на сервере, имеются свойства интеллектуального анализа данных, определяющие поведение конкретных алгоритмов. Настройка этих свойств осуществляется при создании каждой отдельной модели интеллектуального анализа данных, а не на уровне сервера. Дополнительные сведения см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 [Физическая архитектура (службы Analysis Services — интеллектуальный анализ данных)](../data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
