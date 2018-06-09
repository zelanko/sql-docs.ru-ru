---
title: Lag (расширения интеллектуального анализа данных) | Документы Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f984e50b2c6a800a66f689d88b21dfcb487e282
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842497"
---
# <a name="lag-dmx"></a>Lag (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает временной срез между датой текущего варианта и последней датой тренировочного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение целочисленного типа.  
  
## <a name="remarks"></a>Примечания  
 Если **запаздывания** функция используется в модели, где размещен во вложенной таблице столбец KEY TIME, функция должна размещаться внутри вложенного списка выбора инструкции.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает варианты, которые были использованы для обучения модели за последние 12 месяцев.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
