---
description: RangeMin (расширения интеллектуального анализа данных)
title: RangeMin (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 529a669b20719db93ddb702a2b4cff629f53c8db
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500904"
---
# <a name="rangemin-dmx"></a>RangeMin (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает нижнюю точку прогнозируемого сегмента, найденного для дискретизированного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RangeMin(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Применение  
 Скалярные столбцы.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Комментарии  
 Функцию **RangeMin** можно использовать в [инструкции SELECT DISTINCT из модели &#60;&#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md) запросы. При использовании с данным типом запроса ссылка скалярного столбца может содержать непрерывные или дискретные столбцы, являющиеся прогнозируемыми, или входными.  
  
 При использовании с [SELECT из &#60;модели&#62; PREDICTION JOIN &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-from-model-prediction-join-dmx.md), функции **RangeMin**, **RangeMid**и **RangeMax** возвращают фактические граничные значения указанного контейнера. Например, если выполняется прогноз для дискретизированного столбца, запрос возвращает номер прогнозируемого сегмента в дискретизированном столбце. Функции **RangeMin**, **RangeMid**и **RangeMax** описывают контейнер, который указывает прогноз. Если функция **RangeMin** используется с инструкцией PREDICTION JOIN, ссылка на скалярный столбец может содержать только дискретные прогнозируемые столбцы.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает минимальное, максимальное и среднее значение непрерывного столбца Yearly Income модели интеллектуального анализа данных дерева принятия решений.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)   
 [RangeMax &#40;расширений интеллектуального анализа данных&#41;](../dmx/rangemax-dmx.md)   
 [RangeMid &#40;расширений интеллектуального анализа данных&#41;](../dmx/rangemid-dmx.md)  
  
  
