---
title: RangeMax (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 417f92a00e396952218c6ef04d105245f1e3708e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62658982"
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
  
## <a name="remarks"></a>Примечания  
 **RangeMax** функция может использоваться в [SELECT DISTINCT FROM &#60;модели &#62; &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-distinct-from-model-dmx.md) запросов. При использовании с данным типом запроса ссылка скалярного столбца может содержать непрерывные или дискретные столбцы, являющиеся прогнозируемыми, или входными.  
  
 При использовании с [SELECT FROM &#60;модели&#62; PREDICTION JOIN &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-from-model-prediction-join-dmx.md), **RangeMin**, **RangeMid**, и **RangeMax**  функции возвращают фактические граничные значения указанного сегмента. Например, если выполняется прогноз для дискретизированного столбца, запрос возвращает номер прогнозируемого сегмента в дискретизированном столбце. **RangeMin**, **RangeMid**, и **RangeMax** функции описывают сегмент, определенный прогнозом. Когда **RangeMax** функция используется с инструкцией PREDICTION JOIN, ссылка на скалярный столбец может содержать только дискретные, прогнозируемые столбцы.  
  
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
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;расширений интеллектуального анализа данных&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;расширений интеллектуального анализа данных&#41;](../dmx/rangemin-dmx.md)  
  
  
