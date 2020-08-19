---
description: PredictStdev (расширения интеллектуального анализа данных)
title: PredictStdev (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 262533a9c5f4a799bad0f72aee51f1399ba2f483
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422248"
---
# <a name="predictstdev-dmx"></a>PredictStdev (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает прогнозируемое среднеквадратичное отклонение для заданного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictStdev(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Применение  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение типа, заданного параметром *\<scalar column reference>* .  
  
## <a name="remarks"></a>Remarks  
 Если ссылка на столбец является дискретной, **PredictStdev** возвращает 0, так как стандартное отклонение нельзя вычислить из дискретных значений.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется естественное прогнозируемое соединение для определения вероятности покупки велосипеда человеком на основе модели интеллектуального анализа данных TM-дерева принятия решений, а также определяется среднеквадратичное отклонение для этого предсказания.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictStdev([Bike Buyer]) AS [Standard Deviation]  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)  
  
  
