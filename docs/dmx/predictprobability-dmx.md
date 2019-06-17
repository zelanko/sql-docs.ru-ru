---
title: PredictProbability (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f2a01e2cfd460d503e4326c44eaf356b8a5ecb4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62659167"
---
# <a name="predictprobability-dmx"></a>PredictProbability (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает вероятность для указанного состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Примечания  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей вероятностью, за исключением сегмента отсутствующих состояний. Чтобы включить сегмента отсутствующих состояний, установите \<прогнозируемое состояние > для **INCLUDE_NULL**. Для возвращения вероятности для отсутствующих состояний, задайте \<прогнозируемое состояние > в значение NULL.  
  
> [!NOTE]  
>  В некоторых моделях интеллектуального анализа данных значения вероятности не применяются, поэтому в таких моделях нельзя пользоваться этой функцией. Кроме того, значения вероятности для любого конкретного целевого значения рассчитываются по-разному или могут по-разному интерпретироваться в зависимости от типа модели, к которой обращен запрос. Дополнительные сведения о методах расчета вероятности для для конкретного типа модели см. в разделе отдельных алгоритм [содержимое модели интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется естественное прогнозируемое соединение для определения вероятности покупки велосипеда человеком на основе модели интеллектуального анализа данных TM-дерева принятия решений, а также определяется вероятность для этого прогноза. В данном примере имеется две функции PredictProbability — по одной для каждого возможного значения. Если опустить этот аргумент, функция возвратит вероятность наиболее вероятного значения.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Пример результатов:  
  
|Покупатель велосипеда|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
