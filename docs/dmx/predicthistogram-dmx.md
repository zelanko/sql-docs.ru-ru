---
title: PredictHistogram (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fdc63d1c93d1290c701233cb94f71f157c771182
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893852"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает таблицу, представляющую гистограмму прогноза данного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный или кластерный столбец. Может использоваться со всеми типами алгоритмов, за исключением алгоритма взаимосвязей ([!INCLUDE[msCoName](../includes/msconame-md.md)]).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица.  
  
## <a name="remarks"></a>Примечания  
 Гистограмма формирует статистические столбцы. Структура столбца возвращаемой гистограммы зависит от типа ссылки на столбец, который используется с функцией **PredictHistogram** .  
  
## <a name="scalar-columns"></a>Скалярные столбцы  
 Для > ссылки на скалярныйстолбецгистограмма,возвращаемаяфункциейPredictHistogram,состоитизследующих\<столбцов:  
  
-   Прогнозируемое значение  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityVariance**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityStdev**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$AdjustedProbability**  
  
     Столбец **$AdjustedProbability** является [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] расширением [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB для спецификации интеллектуального анализа данных.  
  
## <a name="cluster-columns"></a>Кластерные столбцы  
 Гистограмма, возвращаемая функцией **PredictHistogram** для \<ссылки на столбец кластера > состоит из следующих столбцов:  
  
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
  
## <a name="see-also"></a>См. также  
 [Расширения &#40;интеллектуального анализа данных кластера&#41;](../dmx/cluster-dmx.md)   
 [Расширения &#40;интеллектуального анализа данных ClusterProbability&#41;](../dmx/clusterprobability-dmx.md)   
 [Расширения &#40;интеллектуального анализа данных PredictAdjustedProbability&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [Расширения &#40;интеллектуального анализа данных PredictProbability&#41;](../dmx/predictprobability-dmx.md)   
 [Расширения &#40;интеллектуального анализа данных PredictStdev&#41;](../dmx/predictstdev-dmx.md)   
 [Расширения &#40;интеллектуального анализа данных PredictSupport&#41;](../dmx/predictsupport-dmx.md)   
 [Расширения &#40;интеллектуального анализа данных PredictVariance&#41;](../dmx/predictvariance-dmx.md)   
 [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Справочник по &#40;функциям&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX &#40;-функции&#41;](../dmx/functions-dmx.md)   
 [DMX-функции &#40;общих прогнозирующих функций&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
