---
title: Группы расчета в табличных моделях служб Analysis Services | Документация Майкрософт
ms.date: 06/05/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 58e845965bb9cd4eeba46ad30193c79b436da569
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719867"
---
# <a name="calculation-groups-preview"></a>Группы расчета (Предварительная версия)
 
[!INCLUDE[ssas-appliesto-sql2019](../../includes/ssas-appliesto-sql2019.md)]

Группы расчета может значительно снизить количество избыточных мер, группируя стандартных выражения, как *номенклатуры расчета*. Группы расчета в 1470 и более поздних версий поддерживаются в табличных моделях SQL Server Analysis Services 2019 [уровень совместимости](compatibility-level-for-tabular-models-in-analysis-services.md). Доступных в модели с уровнем совместимости 1470 **предварительной версии**.  

В этой статье рассматриваются следующие вопросы: 

> [!div class="checklist"]
> * Преимущества 
> * Как работают группы расчета
> * Динамический формат строки
> * Приоритет
> * Инструменты
> * Ограничения



## <a name="benefits"></a>Преимущества

Группы расчета устранить проблему в сложных моделей, где может быть большое число избыточных меры, с помощью тех же вычислений — чаще всего вычислений логики операций со временем. Например аналитик продаж хочет просматривать общие объемы продаж и порядков с начала месяца до-(MTD), квартала до даты (с начала Квартала), чтобы год (YTD), упорядочивает года до даты для предыдущего года (PY) и т. д. Разработчик моделей данных должен создать отдельные меры для каждого вычисления, что может привести к десятки меры. Для пользователя это позволяет отсортировать через множество мер и применять их по отдельности в отчет. 

Давайте сначала рассмотрим отображение вычисления групп пользователей в средстве создания отчетов, таких как Power BI. Затем мы рассмотрим том, что такое группа расчета, а также как созданные в модели.

Группы вычисления отображаются в клиентских отчетах как таблица с одним столбцом. Столбец не как типичный столбец или измерение, вместо этого он представляет один или несколько многократно используемых вычислений, или *номенклатуры расчета* , могут применяться к любой мере, уже добавленные к фильтру значения для визуализации.

В следующем анимации пользователь анализ данных о продажах годами, 2012 и 2013. Прежде чем применять группу расчета распространенных базовой мерой **продаж** вычисляет сумму значений от общего объема продаж за каждый месяц. Пользователь хочет применить логику операций со временем вычисления, чтобы получить общие объемы продаж с начала квартала до даты, года, месяца и т. д. Без вычисления групп пользователю нужно выбрать отдельные меры логики операций со временем.

С группой вычисления, в этом примере имеет имя **логики операций со временем**, когда пользователь перетаскивает **расчета времени** элемент **столбцы** область, каждый элемент вычисления фильтров отображается в виде отдельного столбца. Значения для каждой строки вычисляются на основе базовой мерой, **Sales**.  

![Группа расчета применяется в Power BI](media/calculation-groups/calc-groups-pbi.gif)


Группы расчета работать с **явные** меры DAX. В этом примере **Sales** является явной меры, уже созданных в модели. Группы расчета не работают с неявные меры DAX. Например в Power BI неявные меры создаются, когда пользователь перетаскивает столбцов на визуальные элементы для просмотра статистических значений, не создавая явной меры. В настоящее время Power BI создает DAX для неявных мер, написанные как встроенное вычисления DAX — это означает, что неявные меры не может работать с группами вычисления. Новое свойство модели видимой в табличной модели объектов (TOM) был введен, **DiscourageImplicitMeasures**. В настоящее время для создания группы расчета этого свойства должно быть присвоено **true**. Если задано значение true, Power BI Desktop в Live Connect режим отключает создание неявных мер.

## <a name="how-they-work"></a>Как они работают

Теперь, когда вы узнали, как группы расчета полезен для пользователей, давайте рассмотрим создание приведенном примере группа вычислений логики операций со временем.

Прежде чем углубляться в подробности, давайте описываются некоторые новые функции DAX, специально для вычисления групп: 

[SELECTEDMEASURE](https://docs.microsoft.com/dax/selectedmeasure-function-dax) — используется выражения для вычисления элементов для ссылки на меру, которая в настоящее время находится в контексте. В этом примере мере «продажи».

[SELECTEDMEASURENAME](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) — используется выражения для вычисления элементов определить меру, которая находится в контексте по имени.

[ISSELECTEDMEASURE](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) — используется выражения для вычисления товаров, чтобы определить меру, которая находится в контексте, указанные в списке мер.

[SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) — используется выражения для вычисления элементов, извлекаемых в строке формата меру, которая находится в контексте.

### <a name="time-intelligence-example"></a>Пример аналитики времени

Имя таблицы - **логики операций со временем**   
Имя столбца - **расчета времени**   
Приоритет - **20**   

#### <a name="time-intelligence-calculation-items"></a>Номенклатуры расчета времени аналитики

**Current**

```dax
SELECTEDMEASURE()
```

**MTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESMTD(DimDate[Date]))
```

**С НАЧАЛА КВАРТАЛА**

```dax
CALCULATE(SELECTEDMEASURE(), DATESQTD(DimDate[Date]))
```

**С НАЧАЛА ГОДА**

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

**PY**

```dax
CALCULATE(SELECTEDMEASURE(), SAMEPERIODLASTYEAR(DimDate[Date]))
```

**PY MTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "MTD"
)
```

**PY С НАЧАЛА КВАРТАЛА**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "QTD"
)
```

**PY С НАЧАЛА ГОДА**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

**YOY**

```dax
SELECTEDMEASURE() –
CALCULATE(
    SELECTEDMEASURE(),
    'Time Intelligence'[Time Calculation] = "PY"
)
```

**YOY %**

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

Чтобы протестировать эту группу вычисления, можно выполнить запрос DAX в SSMS или с открытым кодом [DAX Studio](http://daxstudio.org/). YOY и YOY % пропущены в этом примере запроса.

#### <a name="time-intelligence-query"></a>Время запроса аналитики

```dax
EVALUATE
CALCULATETABLE (
    SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Current", CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "Current" ),
        "QTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "QTD" ),
        "YTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "YTD" ),
        "PY",      CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY" ),
        "PY QTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY QTD" ),
        "PY YTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY YTD" )
    ),
    DimDate[CalendarYear] IN { 2012, 2013 }
)
```

#### <a name="time-intelligence-query-return"></a>Возвращает время запрос аналитики

Возвращаемой таблицы показывает вычислений для каждого вычисления элемента применяется. Например вы увидите, что с начала Квартала для марта 2012 представляет собой сумму январь, февраль и март 2012 г.

![Ответа на запрос](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>Динамический формат строки

*Динамический формат строки* с расчетом группы позволяют условного применения строки формата к мерам без их нужно возвращать строки.

Табличные модели поддерживают динамическое форматирование мер с помощью DAX [ФОРМАТ](https://docs.microsoft.com/dax/format-function-dax) функции. Однако функцию FORMAT имеет недостатком возвращает строку, принудительной меры, которые в противном случае были бы чисел, чтобы быть возвращены в виде строки. Это может иметь ряд ограничений, например не работает с большинством визуальных элементов Power BI в зависимости от числовых значений, как и диаграммы.

### <a name="dynamic-format-strings-for-time-intelligence"></a>Динамический формат строки для логики операций со временем

Если взглянуть на приведенном выше примере логики операций со временем, все вычисления элементы за исключением **YOY %** следует использовать формат текущей меры в контексте. Например **YTD** из расчета на базовой меры Sales должен быть currency. Если это группа расчета актуально, например заказы базового измерения, то формат будет числовое. **YOY %** , однако должны быть процент независимо от формата базовой мерой.

Для **YOY %** , мы можно переопределить строку формата, задав свойства выражения строки формата **0,00%;-0.00%; 0,00%** . Дополнительные сведения о свойства выражения строки формата, см. в разделе [свойства ячеек многомерных Выражений — содержимое строки ФОРМАТА](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values).

В этот визуальный элемент с матрицей в Power BI, вы увидите **продаж текущего/YOY** и **заказы текущего/YOY** сохранить строки формата их соответствующих базовой мерой. **Продажи YOY %** и **упорядочивает YOY %** , тем не менее, переопределяет строку формата для использования *процент* формат.

![Логика операций со временем в визуальный элемент с матрицей](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>Динамический формат строки для конвертации валют

Динамический формат строки предоставляют простой конвертации. Рассмотрите следующую модель данных Adventure Works. Оно моделируется для *один ко многим* конвертации валют в соответствии с определением [типы конвертации](../currency-conversions-analysis-services.md#conversion-types).

![Курс валюты в табличной модели](media/calculation-groups/calc-groups-currency-conversion.png)

Объект **FormatString** столбец будет добавлен **DimCurrency** таблица и заполняется с помощью строки формата для соответствующих валют.

![Формат строкового столбца](media/calculation-groups/calc-groups-formatstringcolumn.png)

Например следующая группа расчета затем определяется как:

### <a name="currency-conversion-example"></a>Пример преобразования валюты

Имя таблицы - **конвертации валют**   
Имя столбца - **вычислений конвертации**   
Приоритет - **5**   

#### <a name="calculation-items-for-currency-conversion"></a>Вычисление элементов для конвертации валют

**Преобразование не**

```dax
SELECTEDMEASURE()
```

**Преобразованный валюты**

```dax
IF(
    //Check one currency in context & not US Dollar, which is the pivot currency:
    SELECTEDVALUE( DimCurrency[CurrencyName], "US Dollar" ) = "US Dollar",
    SELECTEDMEASURE(),
    SUMX(
        VALUES(DimDate[Date]),
        CALCULATE( DIVIDE( SELECTEDMEASURE(), MAX(FactCurrencyRate[EndOfDayRate]) ) )
    )
)
```

Формат строкового выражения

```dax
SELECTEDVALUE(
    DimCurrency[FormatString],
    SELECTEDMEASUREFORMATSTRING()
)
```
Строковое выражение формата должен возвращать скалярное строковое. Он использует новую [SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) функции, чтобы вернуться к строке формата базовой мерой, при наличии нескольких валют в контекст фильтра.

Следующая анимация демонстрирует преобразование валют динамический формат **Sales** меры в отчете.

![Применить динамический формат строки с преобразования валюты](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>Приоритет

Приоритет имеет свойство, определенное для вычисления группы. Он указывает порядок вычисления, при наличии более чем одна группа расчета. Чем больше число более высокий приоритет, это означает, что оно вычисляется перед группами вычисления с более низким приоритетом.

В этом примере мы будем использовать же модель в качестве приведенный выше пример логики операций со временем, а также добавлять **средние значения** группа расчета. Группа расчета средние значения содержит средних вычислений, которые не зависят от традиционных операций со временем, в том, что они не изменяйте контекст фильтра даты — они просто применить средних вычислений в ней.

В этом примере определяется ежедневно вычисления среднего значения. В приложениях Нефть и газ распространены вычисления, например среднее баррелей масла в день. Другие распространенные бизнеса примеры среднее значение продаж за хранилище в розничной торговле.

Хотя такие вычисления рассчитываются независимо от вычислений логики операций со временем, возможно, имеется требование для их объединения. Например пользователь может потребоваться см. в разделе баррелей масла в день с начала года, чтобы просмотреть частоты ежедневных масла с начала года до текущей даты. В этом случае приоритет должно задаваться для вычисления элементов.

### <a name="averages-example"></a>Пример средние значения

Имя таблицы — **средние значения**.   
Имя столбца является **вычисления среднего значения**.   
Приоритет **10**.   

#### <a name="calculation-items-for-averages"></a>Вычисление элементов для средние значения

**Не среднее значение**

```dax
SELECTEDMEASURE()
```

**Среднее ежедневное значение**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Ниже приведен пример запроса DAX и возвращаемой таблицы:

#### <a name="averages-query"></a>Средние значения запроса

```dax
EVALUATE
    CALCULATETABLE (
        SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Sales", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "No Average"
        ),
        "YTD", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "No Average"
        ),
        "Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "Daily Average"
        ),
        "YTD Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "Daily Average"
        )
    ),
    DimDate[CalendarYear] = 2012
)
```

#### <a name="averages-query-return"></a>Средние значения ответа на запрос

![Ответа на запрос](media/calculation-groups/calc-groups-ytd-daily-avg.png)

Следующей таблице показано, как вычисляются значения март 2012 г.


|Имя столбца  |Вид вычисления |
|---------|---------|
|YTD     |    Отношение суммы продаж для янв, фев, мар 2012<br />= 495,364 + 506,994 + 373,483     |
|Среднее ежедневное значение    |     Продажи для марта 2012, деленное на число дней в марте<br />= 373,483 / 31       |
|Среднее ежедневное значение с начала года     | С начала года для марта 2012, деленное на число дней в янв, фев, мар<br />=  1,375,841 / (31 + 29 + 31)       |

Вот определение номенклатуры расчета с начала года, применяемое с приоритет **20**.

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

Вот ежедневное среднее, с приоритетом из **10**.

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Поскольку приоритет группы расчета логики операций со временем выше, чем группы расчета средние значения, оно будет добавлено как можно более широко. Вычисление YTD ежедневное среднее применяется с начала года для числителя и знаменателя ежедневного вычисления среднего значения (число дней).

Это эквивалентно следующее выражение:

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

Не это выражение:

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>Сторону рекурсии

В приведенном выше примере логики операций со временем некоторые из элементов, вычисления см. для других пользователей в той же группе расчета. Это называется *сторону рекурсии*. Например **YOY %** ссылается на обе **YOY** и **PY**.

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

В этом случае оба выражения вычисляются отдельно, так как они используют разные вычисления инструкций. Другие типы рекурсии не поддерживаются.

## <a name="single-calculation-item-in-filter-context"></a>Один набор вычислений элемента в контекст фильтра

В нашем примере логики операций со временем **PY YTD** номенклатуры расчета имеет единственный вычисления выражения:

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

С начала года аргумент в функцию CALCULATE() переопределяет контекст фильтра для повторного использования логики, уже определен в элементе расчета с начала года. Это не можно применять как PY, так и с начала года в одной оценки. Вычисление группы — *применяется только* Если элементом один набор вычислений на группе расчета находится в контексте фильтра.

## <a name="mdx-support"></a>Поддержка многомерных Выражений

Группы расчета поддерживает запросы Многомерных выражений данных. Это означает, пользователи Microsoft Excel, какие модели табличных данных запроса с помощью многомерных Выражений, можно воспользоваться всеми преимуществами группы расчета таблицы, сводные таблицы и диаграммы.

## <a name="tools"></a>Инструменты

Группы расчета не еще поддерживается в Visual Studio с помощью расширений служб Analysis Services для SQL Server Data Tools. Тем не менее, с помощью модели языка скриптов табличной (TMSL) или открытым исходным кодом, в котором можно создать группы расчета [редактор табличных](https://github.com/otykier/TabularEditor).

## <a name="limitations"></a>Ограничения

[Безопасность на уровне объекта](object-level-security.md) определенные (OLS) для вычисления таблицы групп не поддерживается. Тем не менее можно определить OLS на другие таблицы в той же модели. Если номенклатуру расчета ссылается на объект защищенной OLS, возвращается универсальное сообщение об ошибке.

[Безопасность на уровне строк](roles-ssas-tabular.md#bkmk_rowfliters) (RLS) не поддерживается. Можно определить безопасность на уровне СТРОК в таблицах в той же модели, но не на сами вычисления группы (прямо или косвенно).

[Подробные сведения о выражениях строк](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md) с группы расчета не поддерживаются.

## <a name="see-also"></a>См. также  

[DAX в табличных моделях](understanding-dax-in-tabular-models-ssas-tabular.md)   
[Справочник по языку DAX](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
