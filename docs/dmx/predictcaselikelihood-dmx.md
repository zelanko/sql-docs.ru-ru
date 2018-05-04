---
title: PredictCaseLikelihood (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PredictCaseLikelihood
dev_langs:
- DMX
helpviewer_keywords:
- PredictCaseLikelihood function
ms.assetid: b00180e5-b2eb-49e2-891d-e39fb378f50a
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 06300993d36eb81c6db93e656a7d9ea4cf6e9ff9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Эта функция возвращает правдоподобие того, что входной вариант попадет в существующую модель. Используется только с моделями кластеризации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictCaseLikelihood([NORMALIZED|NONNORMALIZED])  
```  
  
## <a name="arguments"></a>Аргументы  
 NORMALIZED  
 Возвращаемое значение содержит отношение вероятности варианта в рамках модели к вероятности нахождения варианта вне модели.  
  
 NONNORMALIZED  
 Возвращаемое значение содержит необработанное значение вероятности варианта, представляющее собой произведение вероятностей атрибутов варианта.  
  
## <a name="applies-to"></a>Объект применения  
 Модели, построенные с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] кластеризации и [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмы кластеризации последовательностей.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Число с плавающей запятой двойной точности в диапазоне от 0 до 1. Число, более близкое к 1, обозначает большую вероятность вхождения варианта в модель; число, близкое к 0, обозначает меньшую вероятность вхождения варианта в модель.  
  
## <a name="remarks"></a>Замечания  
 По умолчанию, результат **PredictCaseLikelihood** нормализовать функции. Нормализованные значения, как правило, более эффективны, поскольку в варианте увеличивается число атрибутов и разница между необработанными вероятностями двух вариантов существенно уменьшается.  
  
 Следующее уравнение используется для вычисления нормализованных значений при заданных x и y:  
  
-   x = вероятность варианта на основе модели кластеризации;  
  
-   y = вероятность граничного варианта, вычисленная как логарифм правдоподобия варианта на основе подсчета количества обучающих вариантов.  
  
-   Z = Exp( log(x) – Log(Y))  
  
 Нормализованная = (z / (1 + z))  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается правдоподобие вхождения указанного варианта в модель кластеризации, основанную на базе данных [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW.  
  
```  
SELECT  
  PredictCaseLikelihood() AS Default_Likelihood,  
  PredictCaseLikelihood(NORMALIZED) AS Normalized_Likelihood,  
  PredictCaseLikelihood(NONNORMALIZED) AS Raw_Likelihood,  
FROM  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Ожидаемый результат:  
  
|Default_Likelihood|Normalized_Likelihood|Raw_Likelihood|  
|-------------------------|----------------------------|---------------------|  
|6.30672792729321E-08|6.30672792729321E-08|9.5824454056846E-48|  
  
 Разница между результатами демонстрирует влияние нормализации. Необработанное значение **CaseLikelihood** предполагает, что вероятность варианта примерно на 20 процентов; Однако при нормализации результатов становится ясно, что вероятность варианта является очень низким.  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
