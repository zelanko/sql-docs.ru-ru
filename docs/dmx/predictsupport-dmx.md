---
title: "PredictSupport (расширения интеллектуального анализа данных) | Документы Microsoft"
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9bf17c59bfc4f2ef548d695bb5a5710ba5ad249c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="predictsupport-dmx"></a>PredictSupport (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает опорное значение для указанного состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение типа, который задается параметром  *\<* ссылка на скалярный столбец*>*.  
  
## <a name="remarks"></a>Замечания  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей прогнозируемой вероятностью, за исключением сегмента отсутствующих состояний. Для включения сегмента отсутствующих состояний, установите \<прогнозируемое состояние > для **INCLUDE_NULL**.  
  
 Чтобы восстановить поддержку отсутствующих состояний, установите \<прогнозируемое состояние > в NULL.  
  
> [!NOTE]  
>  Значения несущего множества могут рассчитываться или интерпретироваться по-разному в зависимости от типа модели, к которой обращен запрос. Дополнительные сведения о вычислении поддержки для разных типов модели см. в разделе введите в отдельных алгоритм [содержимое модели интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41; ](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

