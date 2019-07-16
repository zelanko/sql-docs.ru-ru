---
title: Кластер (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa7df2782b8102e386c70d5e874a25f7868dbb1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071082"
---
# <a name="cluster-dmx"></a>Cluster (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает кластер, который с наибольшей вероятностью содержит входной вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Объект применения  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **Кластера** функция не требует параметров.  
  
 **Кластера** функция возвращает скалярное значение имени кластера. Тем не менее, при использовании этой функции в качестве аргумента другой функции, с ней необходимо обращаться как \<ссылка на столбец кластера >.  
  
## <a name="remarks"></a>Примечания  
 **Кластер** также может использоваться как `<`ссылка на столбец кластера`>` для **PredictHistogram** функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется одноэлементный запрос с [PredictHistogram &#40;расширений интеллектуального анализа данных&#41; ](../dmx/predicthistogram-dmx.md) и кластера функциями, возвращающими удаленность отдельного из каждого кластера модели интеллектуального анализа данных TM Clustering и вероятность, что отдельного случая будет существовать в каждом кластере.  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также  
 [ClusterProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/clusterprobability-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
