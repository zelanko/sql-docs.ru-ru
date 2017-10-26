---
title: "PredictHistogram (DMX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PredictHistogram
dev_langs:
- DMX
helpviewer_keywords:
- PredictHistogram function
ms.assetid: 85ffc542-96e7-4f58-aaa3-34d76befcedf
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2e0d45b8169d567bbdc69a916f242b2707f6570
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="predicthistogram-dmx"></a>PredictHistogram (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу, представляющую гистограмму прогноза данного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный или кластерный столбец.  Может использоваться со всеми типами алгоритмов, за исключением алгоритма взаимосвязей ([!INCLUDE[msCoName](../includes/msconame-md.md)]).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица.  
  
## <a name="remarks"></a>Замечания  
 Гистограмма формирует статистические столбцы. Структура столбца возвращенной гистограммы зависит от типа ссылки столбца, который используется с **PredictHistogram** функции.  
  
## <a name="scalar-columns"></a>Скалярные столбцы  
 Для \<ссылка на скалярный столбец >, гистограмма, **PredictHistogram** функция возвращает состоит из следующих столбцов:  
  
-   Прогнозируемое значение  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityVariance**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]алгоритмы интеллектуального анализа данных не поддерживают **$ProbabilityStdev**. Этот столбец всегда содержит значение 0 для алгоритмов [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$AdjustedProbability**  
  
     **$AdjustedProbability** столбец [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] расширение [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB для интеллектуального анализа данных.  
  
## <a name="cluster-columns"></a>Кластерные столбцы  
 Гистограмма, **PredictHistogram** функция возвращает для \<ссылка на столбец кластера > состоит из следующих столбцов:  
  
-   **$Cluster** (представляет имя кластера)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает спрогнозированное состояние столбца Bike Buyer в одноэлементном запросе. Этот запрос также возвращает два верхних наиболее вероятных состояния атрибута Bike Buyer, в зависимости от настроенной вероятности, полученной с помощью **PredictHistogram** функции.  
  
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
 [Кластер &#40; расширений интеллектуального анализа данных &#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40; расширений интеллектуального анализа данных &#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40; расширений интеллектуального анализа данных &#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40; расширений интеллектуального анализа данных &#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40; расширений интеллектуального анализа данных &#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40; расширений интеллектуального анализа данных &#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40; расширений интеллектуального анализа данных &#41;](../dmx/predictvariance-dmx.md)   
 [Алгоритмы интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

