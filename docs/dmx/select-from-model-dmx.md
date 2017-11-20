---
title: "SELECT FROM &lt;модель&gt; (DMX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- empty prediction joins [DMX]
- SELECT FROM <model> statement
ms.assetid: dc5b9a01-e308-4ee8-84fc-ba4b991c60aa
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c51d5d3f3a5a1c8e9b94f72367739d592f1918c8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="select-from-ltmodelgt-dmx"></a>SELECT FROM &lt;модель&gt; (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет пустое прогнозируемое соединение и возвращает наиболее вероятные значения для указанных столбцов. Для создания прогноза используется только содержимое модели интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *список выражений*  
 Выражения или прогнозируемые столбцы (включая только предсказываемые), перечисленные через запятую.  
  
 *n*  
 Необязательно. Целое число, указывающее количество возвращаемых строк.  
  
 *model*  
 Идентификатор модели.  
  
 *Список условий*  
 Необязательно. Условия ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательно. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Замечания  
 Столбцы в *список выражений* должен быть задан как прогнозируемый или только прогнозируемый или связанные с прогнозируемым столбцом.  
  
## <a name="naive-bayes-example"></a>Пример упрощенного алгоритма Байеса  
 В приведенном ниже примере выполняется пустое прогнозируемое соединение для столбца Bike Buyer, при этом возвращается наиболее вероятное состояние модели интеллектуального анализа данных TM упрощенного алгоритма Байеса.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Пример алгоритма временных рядов  
 В приведенном ниже примере производится прогнозирование данных столбца Amount модели прогнозирования на четыре последующих шага. В столбце Model Region данные о моделях велосипедов и регионах, объединены в один идентификатор. В запросе используется [PredictTimeSeries &#40; расширений интеллектуального анализа данных &#41;](../dmx/predicttimeseries-dmx.md) функцию для выполнения прогноза.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>См. также:  
 [ВЫБЕРИТЕ &#40; РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ &#41;](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

