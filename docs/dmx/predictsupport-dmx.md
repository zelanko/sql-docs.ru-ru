---
title: PredictSupport (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: da8673d58a6d1889017b0f79ea7cb4bf41c64466
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970702"
---
# <a name="predictsupport-dmx"></a>PredictSupport (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает опорное значение для указанного состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Применение  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение типа, заданного параметром *\<*scalar column reference*>* .  
  
## <a name="remarks"></a>Комментарии  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей прогнозируемой вероятностью, за исключением сегмента отсутствующих состояний. Чтобы включить контейнер отсутствующих состояний, задайте для параметра значение \<predicted state> **INCLUDE_NULL**.  
  
 Чтобы получить поддержку для отсутствующих состояний, присвойте свойству \<predicted state> значение null.  
  
> [!NOTE]  
>  Значения несущего множества могут рассчитываться или интерпретироваться по-разному в зависимости от типа модели, к которой обращен запрос. Дополнительные сведения о вычислении поддержки для любого конкретного типа модели см. в разделе Тип отдельного алгоритма в [содержимом модели интеллектуального анализа данных &#40;Analysis Services-&#41;интеллектуального анализа ](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
## <a name="examples"></a>Примеры  
 Следующий пример использует одноэлементный запрос для прогнозирования вероятности покупки велосипеда каким-либо человеком, а также определяет опорное значение для прогнозирования на основе модели интеллектуального анализа данных TM-дерева принятия решений.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
