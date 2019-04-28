---
title: ClusterProbability (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b8412cf0465594c2546c18990be51510f8938c27
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62706997"
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
  
## <a name="remarks"></a>Примечания  
 Следующий синтаксис использует набор строк схемы содержимого модели интеллектуального анализа данных для возврата заголовков узла, существующего в модели интеллектуального анализа.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Дополнительные сведения об использовании этого синтаксиса см. в разделе [SELECT FROM &#60;модели&#62;. СОДЕРЖИМОГО &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-from-model-content-dmx.md). Дополнительные сведения о наборе строк схемы содержимого модели интеллектуального анализа данных, см. в разделе [набор строк DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
 Если \<заголовок узла > не указан, функция возвращает вероятность, что входной вариант принадлежит к наиболее подходящему кластеру. Используйте **кластера** функция возвращает наиболее вероятного кластера.  
  
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
  
## <a name="see-also"></a>См. также  
 [Кластер &#40;расширений интеллектуального анализа данных&#41;](../dmx/cluster-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
