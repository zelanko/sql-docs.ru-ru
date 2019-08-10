---
title: PredictCaseLikelihood (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0302af7f2241f3e158e8fa95691544c6fdf2dfac
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893919"
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
 Модели, построенные с использованием [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмов кластеризации и [!INCLUDE[msCoName](../includes/msconame-md.md)] кластеризации последовательностей.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Число с плавающей запятой двойной точности в диапазоне от 0 до 1. Число, более близкое к 1, обозначает большую вероятность вхождения варианта в модель; число, близкое к 0, обозначает меньшую вероятность вхождения варианта в модель.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию результат функции **PredictCaseLikelihood** нормализован. Нормализованные значения, как правило, более эффективны, поскольку в варианте увеличивается число атрибутов и разница между необработанными вероятностями двух вариантов существенно уменьшается.  
  
 Следующее уравнение используется для вычисления нормализованных значений при заданных x и y:  
  
-   x = вероятность варианта на основе модели кластеризации;  
  
-   y = вероятность граничного варианта, вычисленная как логарифм правдоподобия варианта на основе подсчета количества обучающих вариантов.  
  
-   Z = exp (log (x) — log (Y))  
  
 Нормализованные = (z/(1 + z))  
  
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
  
 Разница между результатами демонстрирует влияние нормализации. Необработанное значение для **каселикелихуд** предполагает, что вероятность варианта составляет примерно 20 процентов; Однако при нормализации результатов становится очевидно, что вероятность варианта очень мала.  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Справочник по &#40;функциям&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX &#40;-функции&#41;](../dmx/functions-dmx.md)   
 [DMX-функции &#40;общих прогнозирующих функций&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
