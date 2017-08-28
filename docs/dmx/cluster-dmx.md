---
title: "Кластер (DMX) | Документы Microsoft"
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
- Cluster
dev_langs:
- DMX
helpviewer_keywords:
- Cluster function
ms.assetid: 14b2942a-6dec-4dfa-98a6-697a3c89036a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 65e0d6942d48657f99d5cff3365a80d4853c66d4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="cluster-dmx"></a>Cluster (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает кластер, который с наибольшей вероятностью содержит входной вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Объект применения  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **Кластера** функции параметры не требуются.  
  
 **Кластера** функция возвращает скалярное значение имени кластера. Тем не менее, при использовании этой функции в качестве аргумента другой функции с ней необходимо обращаться как \<ссылка на столбец кластера >.  
  
## <a name="remarks"></a>Замечания  
 **Кластер** также может использоваться как `<`ссылка на столбец кластера`>` для **PredictHistogram** функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется одноэлементный запрос с [PredictHistogram &#40; расширений интеллектуального анализа данных &#41;](../dmx/predicthistogram-dmx.md) и кластера функциями, возвращающими удаленность отдельного элемента от каждого кластера модели интеллектуального анализа данных TM Clustering и вероятность существования отдельного элемента в каждом кластере.  
  
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
 [ClusterProbability &#40; расширений интеллектуального анализа данных &#41;](../dmx/clusterprobability-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

