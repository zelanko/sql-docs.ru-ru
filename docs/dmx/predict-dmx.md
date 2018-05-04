---
title: Прогноз (DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PREDICT
dev_langs:
- DMX
helpviewer_keywords:
- Predict function
ms.assetid: f02ff4b3-9bd7-409d-ad14-ead67b3206c4
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6bd1841fa5f4f64e05a6ba4e82464c83d89596f5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="predict-dmx"></a>Predict (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  **Predict** функция возвращает спрогнозированное значение или набор значений для указанного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Ссылка на скалярный столбец или столбец таблицы.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<ссылка на скалярный столбец >  
  
 либо  
  
 \<ссылка на столбец таблицы >  
  
 Тип возвращаемых данных зависит от типа столбца, к которому применяется функция.  
  
> [!NOTE]  
>  Параметры INCLUSIVE, EXCLUSIVE, INPUT_ONLY и INCLUDE_STATISTICS применяются только к ссылкам на столбцы таблицы, а EXCLUDE_NULL и INCLUDE_NULL — только к ссылкам на скалярные столбцы.  
  
## <a name="remarks"></a>Замечания  
 Имеются следующие параметры: EXCLUDE_NULL (по умолчанию), INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (по умолчанию), INPUT_ONLY и INCLUDE_STATISTICS.  
  
> [!NOTE]  
>  Для модели временных рядов функция прогнозирования не поддерживает INCLUDE_STATISTICS.  
  
 Параметр INCLUDE_NODE_ID в качестве результата возвращает столбец $NODEID. NODE_ID является узлом содержимого, на котором прогнозирование осуществляется для определенного объекта. Этот параметр является необязательным при использовании прогноза на основе столбцов таблицы.  
  
 *n* параметр применяется к столбцам таблицы. В зависимости от типа прогноза данный параметр задает количество возвращаемых строк. Если базовые столбцы являются последовательностью, то вызывается **PredictSequence** функции. Если базовые столбцы являются временных рядов, он вызывает метод **PredictTimeSeries** функции. Для ассоциативных типов прогнозирования вызывается **PredictAssociation** функции.  
  
 **Predict** функция поддерживает полиморфизм.  
  
 Часто используются следующие сокращенные формы:  
  
-   [Gender] является альтернативой **Predict**([Gender], EXCLUDE_NULL).  
  
-   [Products Purchases] вместо **Predict**([Products Purchases], EXCLUDE_NULL, EXCLUSIVE).  
  
    > [!NOTE]  
    >  Результатом выполнения данной функции является ссылка на столбец. Это означает, что **Predict** функция может использоваться в качестве аргумента в других функциях, которые принимают в качестве аргумента ссылку на столбец (за исключением **Predict** самой функции).  
  
 Передаче параметра INCLUDE_STATISTICS прогнозу для возвращающих табличные значения столбца добавляет столбцы **$Probability** и **$Support** к результирующей таблице. В данных столбцах содержится сведения о вероятности существования для соответствующей записи вложенной таблицы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция Predict возвращают четырех продуктов в базе данных Adventure Works, которые с наибольшей вероятностью будут проданы совместно. Так как функция осуществляет прогнозирование на основе модели интеллектуального анализа правил взаимосвязи, он автоматически использует **PredictAssociation** работать так, как описано выше.  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 Образец результатов.  
  
 Этот запрос возвращает одну строку данных с одним столбцом, `Expression`, но этот столбец содержит следующую вложенную таблицу.  
  
|Модель|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Фляга для воды|2866|0.192620471805901|0.175205052318795|  
|Ремонтный комплект|2113|0.142012232004839|0.132389356196586|  
|Камера шины для велосипеда Mountain|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
