---
description: BottomSum (расширения интеллектуального анализа данных)
title: BottomSum (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 551fde90989093ab601cfa6100b6c6e208fac9e6
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727753"
---
# <a name="bottomsum-dmx"></a>BottomSum (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает в порядке возрастания ранга нижние строки таблицы, сумма которых является, как минимум, указанным значением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>Применение  
 Выражение, возвращающее таблицу, например \<table column reference> , или функцию, возвращающую таблицу.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<table expression>  
  
## <a name="remarks"></a>Комментарии  
 Функция **BottomSum** возвращает нижние строки в порядке возрастания ранга. Ранг основан на вычисленном значении \<rank expression> аргумента для каждой строки, так что сумма \<rank expression> значений является по крайней мере заданной суммой, заданной \<sum> аргументом. **BottomSum** возвращает наименьшее количество возможных элементов, при этом соблюдая указанное значение Sum.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается прогнозирующий запрос к модели взаимосвязей, построенной с помощью [учебника по базовому интеллектуальному анализу данных](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)).  
  
 Чтобы понять, как работает BottomSum, может оказаться полезным сначала выполнить прогнозирующий запрос, возвращающий только вложенную таблицу.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  В этом примере значение, заданное в качестве входных данных, содержит знак одинарной кавычки, а значит, его нужно экранировать и добавить перед ним еще один знак кавычки. При отсутствии уверенности в синтаксических конструкциях, используемых для вставки escape-символа, запросы можно создавать с помощью построителя прогнозирующих запросов. При выборе значения из раскрывающегося списка необходимый escape-символ вставляется автоматически. Дополнительные сведения см. [в разделе Создание одноэлементного запроса в конструкторе интеллектуального анализа данных](/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
 Пример результатов:  
  
|Модель|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,291283016|0,252695851|  
|Фляга для воды|2866|0,192620472|0,175205052|  
|Ремонтный комплект|2113|0,142012232|0,132389356|  
|Камера шины для велосипеда Mountain|1992|0,133879965|0,125304948|  
|Велосипед Mountain-200|1755|0,117951475|0,111260823|  
|Камера шины для шоссейного велосипеда|1588|0,106727603|0,101229538|  
|Велосипедная шапочка|1473|0,098998589|0,094256014|  
|Набор крыльев для велосипеда Mountain|1415|0,095100477|0,090718432|  
|Держатель фляги для велосипеда Mountain|1367|0,091874454|0,087780332|  
|Держатель фляги для шоссейного велосипеда|1195|0,080314537|0,077173962|  
  
 Функция BottomSum принимает результаты этого запроса и возвращает строки с наименьшими значениями, сумма которых равна указанному счетчику.  
  
```  
SELECT   
BottomSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .1)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Первым аргументом функции BottomSum является имя столбца таблицы. В этом примере вложенная таблица возвращается путем вызова функции Predict и использования аргумента INCLUDE_STATISTICS.  
  
 Вторым аргументом функции BottomSum является столбец во вложенной таблице, который используется для упорядочивания результатов. В этом примере параметр INCLUDE_STATISTICS возвращает столбцы $SUPPORT, $PROBABILTY и $ADJUSTED PROBABILITY. Данный пример использует $PROBABILITY для возврата строк, сумма которых составляет 50% вероятности.  
  
 Третий аргумент функции BottomSum указывает целевую сумму в виде Double. Чтобы получить строки продуктов с минимальным числом, сумма которых составляет 10 процентов вероятности, необходимо ввести 1.  
  
 Пример результатов:  
  
|Модель|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Держатель фляги для шоссейного велосипеда|1195|0,08...|0,07...|  
|Держатель фляги для велосипеда Mountain|1367|0,09...|0,08...|  
  
 **Примечание** . Этот пример предоставляется только для иллюстрации использования BottomSum. В зависимости от размера набора данных выполнение данного запроса может занять значительное время.  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)   
 [BottomPercent &#40;расширений интеллектуального анализа данных&#41;](../dmx/bottompercent-dmx.md)  
  
