---
title: Кластер (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6c14bc8189bdea705ab37c66863d74bcef66e23c
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669819"
---
# <a name="cluster-dmx"></a>Cluster (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает кластер, который с наибольшей вероятностью содержит входной вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Применяется к  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Функция **кластера** не требует параметров.  
  
 Функция **cluster** возвращает скалярное значение имени кластера. Однако при использовании этой функции в качестве аргумента другой функции ее необходимо рассматривать как \< ссылку на столбец кластера>.  
  
## <a name="remarks"></a>Комментарии  
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
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
