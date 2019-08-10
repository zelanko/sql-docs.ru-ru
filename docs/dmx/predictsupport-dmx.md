---
title: PredictSupport (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 701d8fb43b468f6bbd33fbff9ff7cfc8deb386f9
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893828"
---
# <a name="predictsupport-dmx"></a>PredictSupport (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает опорное значение для указанного состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение типа, определяемое *\<* скалярной ссылкой на *>* столбец.  
  
## <a name="remarks"></a>Примечания  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей прогнозируемой вероятностью, за исключением сегмента отсутствующих состояний. Чтобы включить контейнер отсутствующих состояний, задайте \<для прогнозируемого состояния > значение **INCLUDE_NULL**.  
  
 Чтобы получить поддержку для отсутствующих состояний, задайте \<для прогнозируемого состояния > значение null.  
  
> [!NOTE]  
>  Значения несущего множества могут рассчитываться или интерпретироваться по-разному в зависимости от типа модели, к которой обращен запрос. Дополнительные сведения о вычислении поддержки для какого-либо конкретного типа модели см. в разделе Тип отдельного алгоритма в [содержимом &#40;модели интеллектуального&#41;анализа данных Analysis Services — Data Mining](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
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
 [Справочник по &#40;функциям&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX &#40;-функции&#41;](../dmx/functions-dmx.md)   
 [DMX-функции &#40;общих прогнозирующих функций&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
