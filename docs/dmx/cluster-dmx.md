---
description: Cluster (расширения интеллектуального анализа данных)
title: Кластер (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0722e53752cfa01ffee086cb8cf1f6a84f82fd4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457860"
---
# <a name="cluster-dmx"></a>Cluster (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает кластер, который с наибольшей вероятностью содержит входной вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Применение  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Функция **кластера** не требует параметров.  
  
 Функция **cluster** возвращает скалярное значение имени кластера. Однако при использовании этой функции в качестве аргумента другой функции ее необходимо рассматривать как \<cluster column reference> .  
  
## <a name="remarks"></a>Remarks  
 **Кластер** также можно использовать в качестве `<` ссылки на столбец кластера `>` для функции **PredictHistogram** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется одноэлементный запрос с функциями [PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md) и Cluster, чтобы вернуть расстояние отдельного варианта от каждого кластера модели интеллектуального анализа данных с кластеризацией TM и вероятность того, что отдельный вариант будет существовать в каждом кластере.  
  
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
  
## <a name="see-also"></a>См. также:  
 [ClusterProbability &#40;расширений интеллектуального анализа данных&#41;](../dmx/clusterprobability-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)  
  
  
