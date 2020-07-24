---
title: ClusterDistance (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5a4e589455a86f4ffe47e34a6d74d0b6890a5528
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969985"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Функция **ClusterDistance** Возвращает расстояние входного варианта от указанного кластера или значение, если кластер не указан, расстояние входного варианта от наиболее вероятного кластера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>Применение  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию. Эту функцию можно использовать с любой моделью кластеризации (максимизация ожиданий, K-среднее и т. д.), но полученные результаты будут зависеть от алгоритма.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Комментарии  
 Функция **ClusterDistance** Возвращает расстояние между входным вариантом и кластером с наибольшей вероятностью для этого входного варианта.  
  
 В случае кластеризации методом К-средних любой вариант может принадлежать только к одному кластеру с весом членства, равным 1,0, и расстоянием от кластера, всегда равным 0. Однако при использовании метода К-средних предполагается, что каждый кластер имеет центроид. Значение центроида можно получить, выполнив запрос или просмотрев вложенную таблицу NODE_DISTRIBUTION в содержимом модели интеллектуального анализа данных. Дополнительные сведения см. в разделе [Содержимое моделей интеллектуального анализа данных для моделей кластеризации (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining).  
  
 Но если используется применяемый по умолчанию метод кластеризации, называемый методом максимизации ожидания (EM), все точки внутри кластера рассматриваются как равновероятные, так что центроид в кластере отсутствует. Значение **ClusterDistance** между конкретным вариантом и определенным кластером *N* вычисляется следующим образом:  
  
 ClusterDistance (N) = 1-(Мембершипвеигхт (N))  
  
 Или сделайте так:  
  
 ClusterDistance (N) = 1 — ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>Связанные прогнозирующие функции  
 Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] имеют следующие дополнительные функции для запросов к моделям кластеризации.  
  
-   Используйте функцию [cluster &#40;&#41;расширений интеллектуального анализа данных](../dmx/cluster-dmx.md) , чтобы получить наиболее вероятный кластер.  
  
-   Используйте функцию [&#41;расширений интеллектуального анализа данных ClusterProbability &#40;](../dmx/clusterprobability-dmx.md) , чтобы получить вероятность того, что вариант принадлежит конкретному кластеру. Это значение является обратным для расстояния от кластера.  
  
-   Используйте функцию [PredictHistogram &#40;расширений интеллектуального анализа данных&#41;](../dmx/predicthistogram-dmx.md) , чтобы вернуть гистограмму с вероятностью входного варианта, существующего в каждом кластере модели.  
  
-   Используйте функцию [&#41;расширений интеллектуального анализа данных PredictCaseLikelihood &#40;](../dmx/predictcaselikelihood-dmx.md) для возвращения меры от 0 до 1, которая указывает, насколько вероятно, что входной вариант существует, учитывая модель, полученную алгоритмом.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>Example1: получение расстояния от кластера к наиболее вероятному кластеру  
 В следующем примере возвращается расстояние от указанного варианта до кластера, к которому вариант принадлежит с наибольшей вероятностью.  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Пример результатов:  
  
|Expression|  
|----------------|  
|0.0477390930705145|  
  
 Чтобы выяснить, какой это кластер, можно заменить в предыдущем образце функцию `Cluster` на `ClusterDistance`.  
  
 Пример результатов:  
  
|$CLUSTER|  
|--------------|  
|Кластер 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>Example2: получение расстояния для указанного кластера  
 Следующий синтаксис использует набор строк схемы содержимого модели интеллектуального анализа данных для возврата списка идентификаторов узла и заголовков узла для кластеров в модели интеллектуального анализа. Затем можно использовать заголовок Node в качестве аргумента идентификатора кластера в функции **ClusterDistance** .  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 Пример результатов:  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|Кластер 1|  
|002|Кластер 2|  
  
 Следующая синтаксическая конструкция возвращает расстояние до указанного варианта от кластера, обозначенного как Cluster 2.  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Пример результатов:  
  
|Cluster 2 Distance|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>См. также  
 [&#41;расширений интеллектуального анализа данных кластера &#40;](../dmx/cluster-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Содержимое моделей интеллектуального анализа данных для моделей кластеризации (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining)  
  
  
