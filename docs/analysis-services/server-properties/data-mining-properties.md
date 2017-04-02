---
title: "Свойства интеллектуального анализа данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ClusterCount, свойство"
  - "AllowedProvidersInOpenRowset, свойство"
  - "MinimumSeriesValue, свойство"
  - "ScoreMethod, свойство"
  - "MinimumImportance, свойство"
  - "ModellingCardinality, свойство"
  - "BrentTolerance, свойство"
  - "ComplexityPenalty, свойство"
  - "MaximumItemsetCount, свойство"
  - "MinimumSupport, свойство"
  - "AllowSessionMiningModels, свойство"
  - "HoldoutPercentage, свойство"
  - "ClusterCountPrior, свойство"
  - "MaximumSequenceStates, свойство"
  - "OptimizedPredictionCount, свойство"
  - "интеллектуальный анализ данных [службы Analysis Services], свойства"
  - "MaximumStates, свойство"
  - "MaximumContinuousInputAttributes, свойство"
  - "MaximumOutputAttributes, свойство"
  - "AllowAdHocOpenRowsetQueries, свойство"
  - "Enabled, свойство"
  - "HistoricModelGap, свойство"
  - "SampleSize, свойство"
  - "MaximumInputAttributes, свойство"
  - "PeriodicityHint, свойство"
  - "MissingValueSubstitution, свойство"
  - "SplitMethod, свойство"
  - "ForceRegressor, свойство"
  - "MaximumBucketsForContinuousSplit, свойство"
  - "MaxConcurrentPredictionQueries, свойство"
  - "MinimumItemsetSize, свойство"
  - "AcyclicGraph, свойство"
  - "HoldoutMethod, свойство"
  - "StoppingTolerance, свойство"
  - "свойства [интеллектуальный анализ данных]"
  - "AutoDetectPeriodicity, свойство"
  - "HoldoutTolerance, свойство"
  - "MinimumLeafCases, свойство"
  - "HoldoutSeed, свойство"
  - "MinimumClusterCases, свойство"
  - "ClusterCountDeviation, свойство"
  - "MinimumDependencyProbability, свойство"
  - "ClusteringMethod, свойство"
  - "MaximumItemsetSize, свойство"
  - "HiddenNodeRatio, свойство"
  - "MaximumSeriesValue, свойство"
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# Свойства интеллектуального анализа данных
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера интеллектуального анализа данных, перечисленные в следующих таблицах. Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Область применения:** только в многомерном режиме сервера  
  
## Общая категория  
 **AllowSessionMiningModels**  
 Логическое свойство, указывающее, можно ли создать модели интеллектуального анализа данных в сеансах.  
  
 Значение этого свойства по умолчанию равно false, что указывает, что модели интеллектуального анализа данных в сеансах создавать нельзя.  
  
 **AllowAdHocOpenRowsetQueries**  
 Логическое свойство, указывающее, разрешены ли специализированные запросы открытых наборов строк.  
  
 Значение этого свойства по умолчанию равно false, что указывает, что запросы открытых наборов строк не разрешены во время сеанса.  
  
 **AllowedProvidersInOpenRowset**  
 Строковое свойство, идентифицирующее, какие поставщики разрешены в открытом наборе строк, состоящее из списка идентификаторов поставщиков ProgID, разделенного запятыми/точками с запятыми, или из строки «[All]».  
  
 **MaxConcurrentPredictionQueries**  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее максимальное количество параллельных прогнозирующих запросов.  
  
## Категория алгоритмов  
 **Microsoft_Association_Rules\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Association_Rules.  
  
 **Microsoft_Clustering\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Clustering.  
  
 **Microsoft_Decision_Trees\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_DecisionTrees.  
  
 **Microsoft_Naive_Bayes\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Naive_Bayes.  
  
 **Microsoft_Neural_Network\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Neural_Network.  
  
 **Microsoft_Sequence_Clustering\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Sequence_Clustering.  
  
 **Microsoft_Time_Series\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Time_Series.  
  
 **Microsoft_Linear_Regression\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Linear_Regression.  
  
 **Microsoft_Logistic_Regression\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Logistic_Regression.  
  
> [!NOTE]  
>  В дополнение к свойствам, которые определяют доступные службы интеллектуального анализа данных на сервере, имеются свойства интеллектуального анализа данных, определяющие поведение конкретных алгоритмов. Настройка этих свойств осуществляется при создании каждой отдельной модели интеллектуального анализа данных, а не на уровне сервера. Дополнительные сведения см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## См. также  
 [Физическая архитектура (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  