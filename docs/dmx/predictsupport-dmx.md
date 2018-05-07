---
title: PredictSupport (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PredictSupport
dev_langs:
- DMX
helpviewer_keywords:
- PredictSupport function
ms.assetid: 325437d6-7cb5-4ae0-8abe-edb58fe5e90d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17dbe13334a4a11ad14c61b28e34bd32c054dabc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 Скалярное значение типа, который задается параметром *\<* ссылка на скалярный столбец*>*.  
  
## <a name="remarks"></a>Замечания  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей прогнозируемой вероятностью, за исключением сегмента отсутствующих состояний. Для включения сегмента отсутствующих состояний, установите \<прогнозируемое состояние > для **INCLUDE_NULL**.  
  
 Чтобы восстановить поддержку отсутствующих состояний, установите \<прогнозируемое состояние > в NULL.  
  
> [!NOTE]  
>  Значения несущего множества могут рассчитываться или интерпретироваться по-разному в зависимости от типа модели, к которой обращен запрос. Дополнительные сведения о вычислении поддержки для разных типов модели см. в разделе введите в отдельных алгоритм [содержимое модели интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
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
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
