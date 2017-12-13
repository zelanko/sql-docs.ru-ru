---
title: "Занятие 7: Создание мер | Документы Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 28d9d9b4cda3c97a555cce45db525cfb4a6c26f5
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-6-create-measures"></a>Занятие 6. Создание мер
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим меры, которые можно будет добавить в модель. Как и вычисляемые столбцы, созданный на предыдущем занятии, мера — это вычисление, создаваемое с помощью формулы DAX. Однако в отличие от вычисляемых столбцов меры вычисляются на основе выбранного пользователем *фильтра*, например на основе выбора пользователя, определенного столбца или среза, добавленного в поле «Метки строк» в сводной таблице. Значение для каждой ячейки в фильтре вычисляется с помощью меры. Меры — это мощные гибкие вычисления, которые требуется включить в почти все табличные модели для выполнения динамических вычислений с числовыми данными. Дополнительные сведения см. в разделе [меры](../analysis-services/tabular-models/measures-ssas-tabular.md).  
  
Создание мер будет использовать *сетку мер*. По умолчанию каждая таблица имеет пустую сетку мер. Однако обычно меры для каждой таблицы не создаются. Сетка мер появляется внизу таблицы в конструкторе моделей, когда открыто представление данных. Чтобы скрыть или отобразить сетку мер таблицы, в меню **Таблица** выберите команду **Показать сетку мер**.  
  
Меру можно создать, щелкнув по пустой ячейке в сетке мер и введя DAX-формулу в строке формул. Если после создания формулы нажать клавишу ВВОД, мера появится в ячейке. Меры также можно создавать с помощью стандартной агрегатной функции, щелкнув столбец, а затем кнопку автосуммирования (**∑**) на панели инструментов. Меры, созданные с помощью кнопки автосуммирования появится в ячейке сетки мер непосредственно под столбцом, но могут быть перемещены.  
  
На этом занятии меры будут созданы как с помощью ввода DAX-формулы в строке формул, так и с помощью функции автосуммирования.  
  
Предполагаемое время выполнения данного занятия: **30 минут**  
  
## <a name="prerequisites"></a>Предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятия 5: Создание вычисляемых столбцов](../analysis-services/lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Создание мер  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Чтобы создать меру DaysCurrentQuarterToDate таблицы DimDate  
  
1.  В конструкторе моделей щелкните **DimDate** таблицы.  
  
2.  В сетке мер щелкните верхнюю левую пустую ячейку.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Обратите внимание, верхняя левая ячейка теперь содержит имя меры, **DaysCurrentQuarterToDate**, а затем результат, **92**.
    
      ![как табличных lesson6-newmeasure](../analysis-services/media/as-tabular-lesson6-newmeasure.png) 
    
    В отличие от вычисляемых столбцов причем формулы для мер можно ввести имя меры, следуют запятая, а за ними выражении формулы.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Чтобы создать меру DaysInCurrentQuarter таблицы DimDate  
  
1.  С **DimDate** таблицы все еще активна в конструкторе моделей в сетке мер щелкните пустую ячейку под только что созданной мерой.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Во время создания пропорции сравнения между одним неполным периодом и предыдущим периодом формула должна учитывать пропорцию периода, который истек, и сравнивать ее с той же пропорцией в предыдущем периоде. В этом случае [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] дает пропорцию затраченное за текущий период.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Создание меры InternetDistinctCountSalesOrder таблицы FactInternetSales  
  
1.  Нажмите кнопку **FactInternetSales** таблицы.   
  
2.  Щелкните **SalesOrderNumber** заголовок столбца.  
  
3.  Щелкните стрелку вниз рядом с кнопкой автосуммирования (**∑**) на панели инструментов и выберите формулу **DistinctCount**.  
  
    Функция автосуммирования автоматически создаст меру для выбранного столбца, используя стандартную статистическую формулу DistinctCount.  
    
       ![как табличных lesson6-newmeasure2](../analysis-services/media/as-tabular-lesson6-newmeasure2.png)
  
4.  В сетке мер щелкните новую меру, а затем в **свойства** окна в **имя меры**, переименуйте эту меру в **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Создание дополнительных мер в таблицу FactInternetSales  
  
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
    |InternetTotalFreight|фрахт|Sum|=SUM([фрахт])|  
  
2.  Щелкнув по пустой ячейке в сетке мер, а также с помощью строки формул создайте и назовите следующие меры в порядке.  
  
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
Перейдите к следующему занятию: [занятии 7: Создание ключевых показателей эффективности](../analysis-services/lesson-7-create-key-performance-indicators.md).  

  
