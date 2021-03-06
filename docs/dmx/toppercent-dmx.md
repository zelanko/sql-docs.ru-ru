---
description: TopPercent (расширения интеллектуального анализа данных)
title: TopPercent (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f1193e43a00fc4c20487a92e8df3a9f705fa4490
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726096"
---
# <a name="toppercent-dmx"></a>TopPercent (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Функция **TopPercent** возвращает, в порядке убывания ранга, самые верхние строки таблицы, совокупное значение которых не меньше заданного процентного значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopPercent(<table expression>, <rank expression>, <percent>)  
```  
  
## <a name="applies-to"></a>Применение  
 Выражение, возвращающее таблицу, например \<table column reference> , или функцию, возвращающую таблицу.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<table expression>  
  
## <a name="remarks"></a>Комментарии  
 Функция **TopPercent** Возвращает самые верхние строки в порядке убывания ранга на основе вычисленного значения \<rank expression> аргумента для каждой строки, то есть сумма \<rank expression> значений является по меньшей мере заданной процентной долей, заданной \<percent> аргументом. **TopPercent** возвращает наименьшее количество возможных элементов, при этом соблюдая указанное процентное значение.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается прогнозирующий запрос к модели взаимосвязей, построенной с помощью [учебника по базовому интеллектуальному анализу данных](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)).  
  
 Чтобы понять, как работает TopPercent, может оказаться полезным сначала выполнить прогнозирующий запрос, возвращающий только вложенную таблицу.  
  
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
  
 Функция TopPercent принимает результаты этого запроса и возвращает строки с наибольшими значениями, сумма которых равна указанному проценту.  
  
```  
SELECT   
TopPercent  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    50)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Первым аргументом функции TopPercent является имя столбца таблицы. В этом примере вложенная таблица возвращается путем вызова функции Predict и использования аргумента INCLUDE_STATISTICS.  
  
 Вторым аргументом функции TopPercent является столбец во вложенной таблице, который используется для упорядочивания результатов. В этом примере параметр INCLUDE_STATISTICS возвращает столбцы $SUPPORT, $PROBABILTY и $ADJUSTED PROBABILITY. В этом примере используется столбец $SUPPORT, поскольку значения в нем не являются дробными и их легче проверять.  
  
 Третий аргумент функции TopPercent указывает процент в виде Double. Чтобы получить строки для верхних продуктов, стоимость которых составляет 50 процентов от общей поддержки, необходимо ввести 50.  
  
 Пример результатов:  
  
|Модель|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,29...|0,25...|  
|Фляга для воды|2866|0,19...|0,17...|  
|Ремонтный комплект|2113|0,14...|0,13...|  
|Камера шины для велосипеда Mountain|1992|0,133...|0,12...|  
  
 **Примечание** . Этот пример предоставляется только для иллюстрации использования TopPercent. В зависимости от размера набора данных выполнение данного запроса может занять значительное время.  
  
> [!WARNING]  
>  Функции многомерных выражений для TOPPERCENT и BOTTOMPERCENT могут давать непредвиденные результаты, если значения, используемые для вычисления процентов, содержат отрицательные числа. Это не влияет на функции расширений интеллектуального анализа данных. Дополнительные сведения см. в разделе [BottomPercent &#40;многомерных выражений&#41;](../mdx/bottompercent-mdx.md).  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)  
  
