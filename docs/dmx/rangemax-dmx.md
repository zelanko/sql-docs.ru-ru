---
title: "RangeMax (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RangeMax
dev_langs: DMX
helpviewer_keywords: RangeMax function
ms.assetid: 6798d9d7-c3dc-40fb-bd8e-56cb1a6d0e5f
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 24559ff09a5791897a41627941d0cf98c7c3cabf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="rangemax-dmx"></a>RangeMax (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает верхнюю точку прогнозируемого сегмента, найденного для дискретизированного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярные столбцы.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Remarks  
 **RangeMax** функцию можно использовать в [SELECT DISTINCT FROM &#60; модели &#62; &#40; расширений интеллектуального анализа данных &#41;](../dmx/select-distinct-from-model-dmx.md) запросов. При использовании с данным типом запроса ссылка скалярного столбца может содержать непрерывные или дискретные столбцы, являющиеся прогнозируемыми, или входными.  
  
 При использовании с [SELECT FROM &#60; модели &#62; ПРОГНОЗИРУЕМОЕ соединение &#40; расширений интеллектуального анализа данных &#41; ](../dmx/select-from-model-prediction-join-dmx.md), **RangeMin**, **RangeMid**, и **RangeMax** функции возвращают фактические граничные значения указанного сегмента. Например, если выполняется прогноз для дискретизированного столбца, запрос возвращает номер прогнозируемого сегмента в дискретизированном столбце. **RangeMin**, **RangeMid**, и **RangeMax** описывают сегмент, определенный прогнозом. Когда **RangeMax** функция используется с инструкцией PREDICTION JOIN, ссылка на скалярный столбец может содержать только дискретные, прогнозируемые столбцы.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает минимальное, максимальное и среднее значение непрерывного столбца Yearly Income модели интеллектуального анализа данных дерева принятия решений.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemin-dmx.md)  
  
  
