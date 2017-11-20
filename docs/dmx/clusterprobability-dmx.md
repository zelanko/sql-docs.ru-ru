---
title: "ClusterProbability (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ClusterProbability
dev_langs:
- DMX
helpviewer_keywords:
- ClusterProbability function
ms.assetid: a6447b3c-94ce-4122-a3eb-6f3827598d8f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b7f68000caa8fd90dd2a2396ff17f0fd701b96d2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="clusterprobability-dmx"></a>ClusterProbability (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает вероятность того, что входной вариант принадлежит определенному кластеру.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>Объект применения  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Замечания  
 Следующий синтаксис использует набор строк схемы содержимого модели интеллектуального анализа данных для возврата заголовков узла, существующего в модели интеллектуального анализа.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Дополнительные сведения об использовании этого синтаксиса см. в разделе [SELECT FROM &#60; модели &#62;. СОДЕРЖИМОЕ &#40; расширений интеллектуального анализа данных &#41; ](../dmx/select-from-model-content-dmx.md). Дополнительные сведения о наборе строк схемы содержимого модели интеллектуального анализа данных см. в разделе [набор строк DMSCHEMA_MINING_MODEL_CONTENT](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md).  
  
 Если \<заголовок узла > не указан, функция возвращает вероятность того, что входной вариант принадлежит к наиболее подходящему кластеру. Используйте **кластера** функция, возвращающая наиболее вероятного кластера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается вероятность того, что определенный вариант существует в кластере, обозначенном как Cluster 2.  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также:  
 [Кластер &#40; расширений интеллектуального анализа данных &#41;](../dmx/cluster-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

