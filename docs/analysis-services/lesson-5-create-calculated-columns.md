---
title: 'Урок 6: Создание вычисляемых столбцов | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c3b86f84567e85fb604883e7cd7f8de83feb252e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017791"
---
# <a name="lesson-5-create-calculated-columns"></a>Занятие 5. Создание вычисляемых столбцов
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим новые данные в модели путем добавления вычисляемых столбцов. Вычисляемый столбец основывается на данных, которые уже существуют в модели. Дополнительные сведения см. в разделе [Calculated Columns](../analysis-services/tabular-models/ssas-calculated-columns.md).  
  
Мы создадим пять новых вычисляемых столбцов в трех разных таблицах. Шаги выполнения для каждой задачи могут немного отличаться друг от друга. Это сделано для того, чтобы продемонстрировать разные способы создания новых столбцов, переименовывания и размещения в разных местах в таблице.  
  
Предполагаемое время выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>Предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятия 4: Создание связей](../analysis-services/lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Создание вычисляемых столбцов  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца MonthCalendar таблицы DimDate  
  
1.  Нажмите кнопку **модели** меню > **представление модели** > **представление данных**.  
  
    Вычисляемые столбцы можно создавать только с помощью конструктора моделей в представлении данных.  
  
2.  В конструкторе моделей щелкните **DimDate** таблицу (вкладку).  
  
3.  Щелкните правой кнопкой мыши **CalendarQuarter** заголовок столбца, а затем щелкните **вставить столбец**.  
  
    Новый столбец с именем **Вычисляемый столбец 1** будет вставлен слева от столбца **Календарный квартал** .  
  
4.  В строке формул над таблицей введите следующую формулу. Автозаполнение помогает вводить полные имена столбцов и таблиц, а также выводит список доступных функций.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Все строки вычисляемого столбца будут заполнены значениями. При прокрутке таблицы вниз будет видно, что строки могут содержать различные значения для данного столбца, на основе данных, которые содержатся в каждой строке.    
  
5.  Переименовать этот столбец в **MonthCalendar**. 

    ![как табличных lesson5-newcolumn](../analysis-services/media/as-tabular-lesson5-newcolumn.png) 
  
MonthCalendar вычисляемый столбец содержит сортируемое имя для месяца.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца DayOfWeek таблицы DimDate  
  
1.  С **DimDate** активной таблице можно, щелкнув **столбца** меню, а затем нажмите **добавить столбец**.  
  
2.  В строке формул введите следующую формулу:  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    Завершив построение формулы, нажмите клавишу ВВОД. Новый столбец будет добавлен на самой правой стороне таблицы.  
  
3.  Переименуйте столбец в **DayOfWeek**.  
  
4.  Щелкните заголовок столбца, а затем перетащите столбец между столбцами **EnglishDayNameOfWeek** столбца и **DayNumberOfMonth** столбца.  
  
    > [!TIP]  
    > Перемещение столбцов в таблице облегчает навигацию.  
  
DayOfWeek вычисляемый столбец содержит сортируемое имя дня недели.  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>Создание вычисляемого столбца ProductSubcategoryName в таблице DimProduct  
  
  
1.  В **DimProduct** таблицы, прокрутите до правого края таблицы. Обратите внимание на то, что крайний правый столбец имеет имя **Добавление столбца** (курсивом), и щелкните заголовок столбца.  
  
2.  В строке формул введите следующую формулу:  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Переименуйте столбец в **ProductSubcategoryName**.  
  
Вычисляемый столбец ProductSubcategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductSubcategoryName DimProductSubcategory таблицы. Иерархии не могут охватывать более одной таблицы. Иерархии будут созданы позже в занятии 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Создание вычисляемого столбца ProductCategoryName в таблице DimProduct  
  
1.  С **DimProduct** еще активен, щелкните таблицу **столбца** меню, а затем нажмите **добавить столбец**.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Переименуйте столбец в **ProductCategoryName**.  
  
Вычисляемый столбец ProductCategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductCategoryName DimProductCategory таблицы. Иерархии не могут охватывать более одной таблицы.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Создание вычисляемого столбца поля таблицы FactInternetSales  
  
1.  В конструкторе моделей выберите **FactInternetSales** таблицы.  
  
2.  Добавление нового столбца.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Переименуйте столбец в **Маржа**.  
  
5.  Перетащите столбец между **SalesAmount** столбца и **TaxAmt** столбца. 
 
      ![как табличных lesson5-newmargin](../analysis-services/media/as-tabular-lesson5-newmargin.png)
      
    Вычисляемый столбец поле используется для анализа маржи для каждой продажи.  
  
## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [Lesson 6: Создание меры](../analysis-services/lesson-6-create-measures.md).
  
  
  
