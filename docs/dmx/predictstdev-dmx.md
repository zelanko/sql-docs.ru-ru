---
title: PredictStdev (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 56d8ade3b270f1e81cb2ac0455a245bd78cacd70
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659010"
---
# <a name="predictstdev-dmx"></a>PredictStdev (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает прогнозируемое среднеквадратичное отклонение для заданного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictStdev(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение типа, который задается параметром  *\<ссылка на скалярный столбец >*.  
  
## <a name="remarks"></a>Примечания  
 Если ссылка на столбец является дискретной, **PredictStdev** возвращает 0, так как невозможно вычислить среднеквадратичное отклонение по дискретным значениям.  
  
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
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
