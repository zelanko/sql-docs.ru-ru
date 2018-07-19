---
title: 'Занятие 7: Создание мер | Документация Майкрософт'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 146d93bc2c7257ce409f3a293f6c9050acde9ca7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994966"
---
# <a name="lesson-6-create-measures"></a>Занятие 6. Создание мер
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим меры, которые можно будет добавить в модель. Как и вычисляемые столбцы, которые вы создали на предыдущем занятии, мера представляет собой вычисление, созданное с помощью формулы DAX. Однако в отличие от вычисляемых столбцов меры вычисляются на основе выбранного пользователем *фильтра*, например на основе выбора пользователя, определенного столбца или среза, добавленного в поле «Метки строк» в сводной таблице. Значение для каждой ячейки в фильтре вычисляется с помощью меры. Меры — это эффективные и гибкие средства вычисления, которые требуется включить в почти в любых табличных моделях для динамических расчетов с числовыми данными. Дополнительные сведения см. в разделе [меры](../analysis-services/tabular-models/measures-ssas-tabular.md).  
  
Создание мер будет использоваться *сетку мер*. По умолчанию каждая таблица имеет пустую сетку мер. Однако обычно меры для каждой таблицы не создаются. Сетка мер появляется внизу таблицы в конструкторе моделей, когда открыто представление данных. Чтобы скрыть или отобразить сетку мер таблицы, в меню **Таблица** выберите команду **Показать сетку мер**.  
  
Меру можно создать, щелкнув по пустой ячейке в сетке мер и введя DAX-формулу в строке формул. Если после создания формулы нажать клавишу ВВОД, мера появится в ячейке. Меры также можно создавать с помощью стандартной агрегатной функции, щелкнув столбец, а затем кнопку автосуммирования (**∑**) на панели инструментов. Меры, созданные с помощью функции "Автосумма" будет отображаться в ячейке сетки мер непосредственно под столбцом, но их можно перемещать.  
  
На этом занятии меры будут созданы как с помощью ввода DAX-формулы в строке формул, так и с помощью функции автосуммирования.  
  
Предполагаемое время выполнения данного занятия: **30 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [занятия 5: Создание вычисляемых столбцов](../analysis-services/lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Создание мер  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Создание меры DaysCurrentQuarterToDate в таблице DimDate  
  
1.  В конструкторе моделей щелкните **DimDate** таблицы.  
  
2.  В сетке мер щелкните верхнюю левую пустую ячейку.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Обратите внимание, что верхняя левая ячейка теперь содержит имя меры, **DaysCurrentQuarterToDate**, а затем результат **92**.
    
      ![как табличных lesson6-newmeasure](../analysis-services/media/as-tabular-lesson6-newmeasure.png) 
    
    В отличие от вычисляемых столбцов формул мер можно ввести имя меры, следует запятая, а затем выражение формулы.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Создание меры DaysInCurrentQuarter в таблице DimDate  
  
1.  С помощью **DimDate** таблицы все еще активна в конструкторе моделей в сетке мер щелкните пустую ячейку под только что созданной мерой.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Во время создания пропорции сравнения между одним неполным периодом и предыдущим периодом формула должна учитывать пропорцию периода, который истек, и сравнивать ее с той же пропорцией в предыдущем периоде. В этом случае [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] дает пропорцию, прошедшую в текущем периоде.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Создание меры InternetDistinctCountSalesOrder в таблице FactInternetSales  
  
1.  Нажмите кнопку **FactInternetSales** таблицы.   
  
2.  Щелкните **SalesOrderNumber** заголовок столбца.  
  
3.  Щелкните стрелку вниз рядом с кнопкой автосуммирования (**∑**) на панели инструментов и выберите формулу **DistinctCount**.  
  
    Функция автосуммирования автоматически создаст меру для выбранного столбца, используя стандартную статистическую формулу DistinctCount.  
    
       ![как табличных lesson6-newmeasure2](../analysis-services/media/as-tabular-lesson6-newmeasure2.png)
  
4.  В сетке мер щелкните новую меру, а затем в **свойства** окно в **имя меры**, переименуйте эту меру в **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Создание дополнительных мер в таблице FactInternetSales  
  
1.  Создайте и назовите следующие меры, используя функцию автосуммирования.  
  
    |Имя меры|Столбец|Автосуммирование (∑)|Формула|  
    |----------------|----------|-----------------|-----------|  
    |InternetOrderLinesCount|SalesOrderLineNumber|Count|=COUNTA([SalesOrderLineNumber])|  
    |InternetTotalUnits|OrderQuantity|SUM|=SUM([OrderQuantity])|  
    |InternetTotalDiscountAmount|DiscountAmount|SUM|=SUM([DiscountAmount])|  
    |InternetTotalProductCost|TotalProductCost|SUM|=SUM([TotalProductCost])|  
    |InternetTotalSales|SalesAmount|SUM|=SUM([SalesAmount])|  
    |InternetTotalMargin|Маржа|SUM|=SUM([маржа])|  
    |InternetTotalTaxAmt|TaxAmt|SUM|=SUM([TaxAmt])|  
    |InternetTotalFreight|Freight|SUM|=SUM([фрахт])|  
  
2.  Щелкнув пустую ячейку в сетке мер или с помощью строки формул создайте и назовите следующие меры в указанном порядке:  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
Меры, созданные для таблицы FactInternetSales может использоваться для анализа критических финансовых данных, таких как продажи, затраты и прибыли для элементов, определенных с помощью выбранного пользователем фильтра.  
  
## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятии 7: Создание ключевых показателей эффективности](../analysis-services/lesson-7-create-key-performance-indicators.md).  

  
