---
title: 'Занятие 6: Создание мер | Документация Майкрософт'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f8ad53f78acb862101ff633f663ea03198825ab
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404666"
---
# <a name="lesson-6-create-measures"></a>Занятие 6: Создание мер
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим меры, которые можно будет добавить в модель. Как и вычисляемые столбцы, которые вы создали на предыдущем занятии, мера представляет собой вычисление, созданное с помощью формулы DAX. Однако в отличие от вычисляемых столбцов меры вычисляются на основе выбранного пользователем *фильтра*, например на основе выбора пользователя, определенного столбца или среза, добавленного в поле «Метки строк» в сводной таблице. Значение для каждой ячейки в фильтре вычисляется с помощью меры. Меры — это эффективные и гибкие средства вычисления, которые требуется включить в почти в любых табличных моделях для динамических расчетов с числовыми данными. Дополнительные сведения см. в разделе [меры](../tabular-models/measures-ssas-tabular.md).  
  
Создание мер будет использоваться *сетку мер*. По умолчанию каждая таблица имеет пустую сетку мер. Однако обычно меры для каждой таблицы не создаются. Сетка мер появляется внизу таблицы в конструкторе моделей, когда открыто представление данных. Чтобы скрыть или отобразить сетку мер таблицы, в меню **Таблица** выберите команду **Показать сетку мер**.  
  
Меру можно создать, щелкнув по пустой ячейке в сетке мер и введя DAX-формулу в строке формул. Если после создания формулы нажать клавишу ВВОД, мера появится в ячейке. Меры также можно создавать с помощью стандартной агрегатной функции, щелкнув столбец, а затем кнопку автосуммирования (**∑**) на панели инструментов. Меры, созданные с помощью функции "Автосумма" будет отображаться в ячейке сетки мер непосредственно под столбцом, но их можно перемещать.  
  
На этом занятии меры будут созданы как с помощью ввода DAX-формулы в строке формул, так и с помощью функции автосуммирования.  
  
Предполагаемое время для выполнения этого занятия: **30 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 5. Создание вычисляемых столбцов](lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Создание мер  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Создание меры DaysCurrentQuarterToDate в таблице DimDate  
  
1.  В конструкторе моделей щелкните **DimDate** таблицы.  
  
2.  В сетке мер щелкните верхнюю левую пустую ячейку.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Обратите внимание, что верхняя левая ячейка теперь содержит имя меры, **DaysCurrentQuarterToDate**, а затем результат **92**.
    
      ![как табличных lesson6-newmeasure](media/as-tabular-lesson6-newmeasure.png) 
    
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
    
       ![как табличных lesson6-newmeasure2](media/as-tabular-lesson6-newmeasure2.png)
  
4.  В сетке мер щелкните новую меру, а затем в **свойства** окно в **имя меры**, переименуйте эту меру в **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Создание дополнительных мер в таблице FactInternetSales  
  
1.  Создайте и назовите следующие меры, используя функцию автосуммирования.  
  
    |Имя меры|Столбец|Автосуммирование (∑)|Формула|  
    |----------------|----------|-----------------|-----------|  
    |InternetOrderLinesCount|SalesOrderLineNumber|Count|=COUNTA([SalesOrderLineNumber])|  
    |InternetTotalUnits|OrderQuantity|Sum|=SUM([OrderQuantity])|  
    |InternetTotalDiscountAmount|DiscountAmount|Sum|=SUM([DiscountAmount])|  
    |InternetTotalProductCost|TotalProductCost|Sum|=SUM([TotalProductCost])|  
    |InternetTotalSales|SalesAmount|Sum|=SUM([SalesAmount])|  
    |InternetTotalMargin|Маржа|Sum|=SUM([маржа])|  
    |InternetTotalTaxAmt|TaxAmt|Sum|=SUM([TaxAmt])|  
    |InternetTotalFreight|Freight|Sum|=SUM([фрахт])|  
  
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
Перейдите к следующему занятию: [Занятие 7. Создание ключевых показателей эффективности](lesson-7-create-key-performance-indicators.md).  

  
