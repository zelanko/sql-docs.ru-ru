---
description: ClusterProbability (расширения интеллектуального анализа данных)
title: ClusterProbability (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cb2cc218ff18b23237c561a3cac1a9a68373f3ae
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726330"
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает вероятность того, что входной вариант принадлежит определенному кластеру.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>Применение  
 Эту функцию можно использовать только в случае, если базовая модель интеллектуального анализа данных поддерживает кластеризацию.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Комментарии  
 Следующий синтаксис использует набор строк схемы содержимого модели интеллектуального анализа данных для возврата заголовков узла, существующего в модели интеллектуального анализа.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Дополнительные сведения об использовании этого синтаксиса см [. в разделе Выбор из &#60;модели&#62;. CONTENT &#40;&#41;расширений интеллектуального анализа данных ](../dmx/select-from-model-content-dmx.md). Дополнительные сведения о наборе строк схемы содержимого модели интеллектуального анализа данных см. в разделе [DMSCHEMA_MINING_MODEL_CONTENT набор строк](/previous-versions/sql/sql-server-2012/ms126267(v=sql.110)).  
  
 Если \<node caption> аргумент не указан, функция возвращает вероятность того, что входные варианты принадлежат к наиболее вероятному кластеру. Используйте функцию **cluster** для возврата наиболее вероятного кластера.  
  
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
 [&#41;расширений интеллектуального анализа данных кластера &#40;](../dmx/cluster-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)  
  
