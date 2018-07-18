---
title: ClusterDistance (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2d8eb879d23a344e5de6bad3c9fb6042fdadb3e7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985400"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  **ClusterDistance** функция возвращает расстояние входного варианта от указанного кластера, или если кластер не указан, расстояние до входного варианта от наиболее вероятного кластера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>Объект применения  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию. Эту функцию можно использовать с любой моделью кластеризации (максимизация ожиданий, K-среднее и т. д.), но полученные результаты будут зависеть от алгоритма.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Примечания  
 **ClusterDistance** функция возвращает расстояние между входным вариантом и кластером с наибольшей вероятностью для данного входного варианта.  
  
 В случае кластеризации методом К-средних любой вариант может принадлежать только к одному кластеру с весом членства, равным 1,0, и расстоянием от кластера, всегда равным 0. Однако при использовании метода К-средних предполагается, что каждый кластер имеет центроид. Значение центроида можно получить, выполнив запрос или просмотрев вложенную таблицу NODE_DISTRIBUTION в содержимом модели интеллектуального анализа данных. Дополнительные сведения см. в разделе [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md).  
  
 Но если используется применяемый по умолчанию метод кластеризации, называемый методом максимизации ожидания (EM), все точки внутри кластера рассматриваются как равновероятные, так что центроид в кластере отсутствует. Значение **ClusterDistance** между конкретным вариантом и определенному кластеру *N* вычисляется следующим образом:  
  
 ClusterDistance(N) =1–(membershipWeight(N))  
  
 или:  
  
 ClusterDistance(N) = 1 — ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>Связанные прогнозирующие функции  
 Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] имеют следующие дополнительные функции для запросов к моделям кластеризации.  
  
-   Используйте [кластера &#40;расширений интеллектуального анализа данных&#41; ](../dmx/cluster-dmx.md) функция возвращает наиболее вероятного кластера.  
  
-   Используйте [ClusterProbability &#40;расширений интеллектуального анализа данных&#41; ](../dmx/clusterprobability-dmx.md) функцию, чтобы получить вероятность принадлежности варианта определенному кластеру. Это значение является обратным для расстояния от кластера.  
  
-   Используйте [PredictHistogram &#40;расширений интеллектуального анализа данных&#41; ](../dmx/predicthistogram-dmx.md) функцию для возврата гистограммы вероятности существует входной вариант в каждом кластере модели.  
  
-   Используйте [PredictCaseLikelihood &#40;расширений интеллектуального анализа данных&#41; ](../dmx/predictcaselikelihood-dmx.md) функция, возвращающая мера от 0 до 1, указывающей вероятность входной вариант — существует, учитывая модель, обученную этим алгоритмом.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>Пример 1: Вычисление расстояния до наиболее вероятного кластера  
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
  
|Выражение|  
|----------------|  
|0.0477390930705145|  
  
 Чтобы выяснить, какой это кластер, можно заменить в предыдущем образце функцию `Cluster` на `ClusterDistance`.  
  
 Пример результатов:  
  
|$CLUSTER|  
|--------------|  
|Кластер 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>Example2: Получение расстояния до указанного кластера  
 Следующий синтаксис использует набор строк схемы содержимого модели интеллектуального анализа данных для возврата списка идентификаторов узла и заголовков узла для кластеров в модели интеллектуального анализа. Затем можно использовать заголовок узла в качестве аргумента идентификатора кластера в **ClusterDistance** функции.  
  
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
 [Кластер &#40;расширений интеллектуального анализа данных&#41;](../dmx/cluster-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Содержимое модели интеллектуального анализа данных для моделей кластеризации &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
