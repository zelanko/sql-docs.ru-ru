---
title: Запаздывание (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 170e2f8b565f8b3d9d5e385b2bba9f183e743ace
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008356"
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
  
## <a name="remarks"></a>Remarks  
 Если функция **Lag** используется в модели, где ключевой столбец времени находится внутри вложенной таблицы, функция должна находиться внутри подзапроса инструкции.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает варианты, которые были использованы для обучения модели за последние 12 месяцев.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
