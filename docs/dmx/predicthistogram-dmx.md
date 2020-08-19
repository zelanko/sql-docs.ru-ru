---
description: PredictHistogram (расширения интеллектуального анализа данных)
title: PredictHistogram (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ecc213e023483245fb8b40a55de749c23ae16a84
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426166"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает таблицу, представляющую гистограмму прогноза данного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>Применение  
  Скалярный или кластерный столбец.  Может использоваться со всеми типами алгоритмов, за исключением алгоритма взаимосвязей ([!INCLUDE[msCoName](../includes/msconame-md.md)]).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица.  
  
## <a name="remarks"></a>Remarks  
 Гистограмма формирует статистические столбцы. Структура столбца возвращаемой гистограммы зависит от типа ссылки на столбец, который используется с функцией **PredictHistogram** .  
  
## <a name="scalar-columns"></a>Скалярные столбцы  
 Для \<scalar column reference> , гистограмма, возвращаемая функцией **PredictHistogram** , состоит из следующих столбцов:  
  
-   Прогнозируемое значение  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityVariance**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityStdev**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$AdjustedProbability**  
  
     Столбец **$AdjustedProbability** является [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] расширением [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB для спецификации интеллектуального анализа данных.  
  
## <a name="cluster-columns"></a>Кластерные столбцы  
 Гистограмма, возвращаемая функцией **PredictHistogram** для, \<cluster column reference> состоит из следующих столбцов:  
  
-   **$Cluster** (представляет имя кластера)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает спрогнозированное состояние столбца Bike Buyer в одноэлементном запросе. Запрос также возвращает первые два наиболее вероятных состояния атрибута Bike Buyer на основе скорректированной вероятности, полученной с помощью функции **PredictHistogram** .  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также:  
 [&#41;расширений интеллектуального анализа данных кластера &#40;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;расширений интеллектуального анализа данных&#41;](../dmx/predictvariance-dmx.md)   
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)  
  
  
