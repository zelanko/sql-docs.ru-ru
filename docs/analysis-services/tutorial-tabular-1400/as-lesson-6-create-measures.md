---
title: 'Занятие учебника Analysis Services 6: создание мер | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fcb305b93d90d83975701e0943542b95ea6c244e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-measures"></a>Создание мер

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии вы создаете меры для включения в модель. Как и вычисляемые столбцы, которые вы создали, мера — это вычисление, создаваемое с помощью формулы DAX. Однако в отличие от вычисляемых столбцов меры вычисляются на основе пользователь выбрал *фильтра*. Например определенного столбца или среза, добавленного в поле метки строк в сводной таблице. Значение для каждой ячейки в фильтре вычисляется с помощью меры. Меры — это мощные гибкие вычисления, которые требуется включить почти все табличные модели для выполнения динамических вычислений с числовыми данными. Дополнительные сведения см. в разделе [меры](../tabular-models/measures-ssas-tabular.md).
  
Создание мер производится *сетку мер*. По умолчанию каждая таблица имеет пустую сетку мер; Тем не менее обычно не меры создаются для каждой таблицы. Сетка мер появляется внизу таблицы в конструкторе моделей, когда открыто представление данных. Чтобы скрыть или отобразить сетку мер таблицы, в меню **Таблица** выберите команду **Показать сетку мер**.  
  
Можно создать меру, щелкнув пустую ячейку в сетке мер и введя DAX-формулу в строке формул. Если нажать клавишу ВВОД для завершения формулы мера, то отображается в ячейке. Можно также создать меры, используя стандартную статистическую функцию, щелкнув столбец и затем нажать кнопку автосуммирования (**∑**) на панели инструментов. Меры, созданные с помощью кнопки автосуммирования отображается в ячейке сетки мер непосредственно под столбцом, но могут быть перемещены.  
  
На этом занятии вы создаете меры обоих ввода формулы DAX в строке формул, а также с помощью функции автосуммирования.  
  
Предполагаемое время выполнения данного занятия: **30 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятия 5: Создание вычисляемых столбцов](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Создание мер  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Чтобы создать меру DaysCurrentQuarterToDate таблицы DimDate  
  
1.  В конструкторе моделей щелкните **DimDate** таблицы.  
  
2.  В сетке мер щелкните верхнюю левую пустую ячейку.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Обратите внимание, верхняя левая ячейка теперь содержит имя меры, **DaysCurrentQuarterToDate**, а затем результат, **92**. Результат не применимо к этому моменту, так как был применен фильтр не пользователя.
    
      ![как newmeasure lesson6](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    В отличие от вычисляемых столбцов причем формулы для мер можно ввести имя меры, за которым следует двоеточие, следуют выражении формулы.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Чтобы создать меру DaysInCurrentQuarter таблицы DimDate  
  
1.  С **DimDate** таблицы все еще активна в конструкторе моделей в сетке мер щелкните пустую ячейку под созданную меру.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Во время создания пропорции сравнения между одним неполным периодом и предыдущим периодом. Формула вычисляет долю периода времени и сравнивать ее с той же пропорцией в предыдущем периоде. В этом случае [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] дает пропорцию затраченное за текущий период.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Создание меры InternetDistinctCountSalesOrder таблицы FactInternetSales  
  
1.  Нажмите кнопку **FactInternetSales** таблицы.   
  
2.  Нажмите кнопку **SalesOrderNumber** заголовок столбца.  
  
3.  Щелкните стрелку вниз рядом с кнопкой автосуммирования (**∑**) на панели инструментов и выберите формулу **DistinctCount**.  
  
    Функция автосуммирования автоматически создаст меру для выбранного столбца, используя стандартную статистическую формулу DistinctCount.  
    
       ![как newmeasure2 lesson6](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  В сетке мер щелкните новую меру, а затем в **свойства** окна в **имя меры**, переименуйте эту меру в **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Создание дополнительных мер в таблицу FactInternetSales  
  
1.  Создайте и назовите следующие меры, используя функцию автосуммирования.  

    |Столбец|Имя меры|Автосуммирование (∑)|Формула|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Count|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|Sum|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|Sum|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|Sum|=SUM([TotalProductCost])|  
    |SalesAmount|InternetTotalSales|Sum|=SUM([SalesAmount])|  
    |Маржа|InternetTotalMargin|Sum|=SUM([маржа])|  
    |TaxAmt|InternetTotalTaxAmt|Sum|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|Sum|=SUM([фрахт])|  
  
2.  Щелкнув пустую ячейку в сетке мер, а также с помощью строки формул создайте, следующие пользовательские меры в порядке:  
  
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
  
Меры, созданные для таблицы FactInternetSales может использоваться для анализа критических финансовых данных, таких как продажи, издержки и маржа прибыли для элементов, определенных фильтром, выбранным пользователем.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 7: Создание ключевых показателей эффективности](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  

  
