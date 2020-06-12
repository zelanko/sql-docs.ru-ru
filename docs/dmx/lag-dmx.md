---
title: Запаздывание (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 04b06d1cbe14ee83915bd5626337720acf9bd2a9
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670340"
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
  
## <a name="remarks"></a>Комментарии  
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
  
  
