---
title: 'Занятие 5 учебника служб Analysis: Создание вычисляемых столбцов | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8406ff8e3bf6981dedea21f6916101aa42b1061a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-calculated-columns"></a>Создание вычисляемых столбцов

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии были созданы данные в модели путем добавления вычисляемых столбцов. Можно создать вычисляемые столбцы (как пользовательские столбцы) при использовании получение данных, с помощью редактора запросов или более поздней версии в модели конструктора like можно сделать здесь. Дополнительные сведения см. в разделе [вычисляемых столбцов](../tabular-models/ssas-calculated-columns.md).
  
Создайте пять новых вычисляемых столбцов в трех различных таблицах. Шаги немного отличаются для каждой задачи, показывающей, существует несколько способов создания столбцов, переименуйте их и помещать их в разных местах в таблице.  

Это занятие является также, где используется впервые выражений анализа данных (DAX). DAX — это специальные язык для создания настраиваемых формул выражений для табличных моделей. В этом учебнике используется DAX для создания вычисляемых столбцов, меры и фильтры. Дополнительные сведения см. в разделе [DAX в табличных моделях](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md). 
  
Предполагаемое время выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятия 4: Создание связей](../tutorial-tabular-1400/as-lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Создание вычисляемых столбцов  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца MonthCalendar таблицы DimDate  
  
1.  Нажмите кнопку **модели** меню > **представление модели** > **представление данных**.  
  
    Вычисляемые столбцы можно создавать только с помощью конструктора моделей в представлении данных.  
  
2.  В конструкторе моделей щелкните **DimDate** таблицу (вкладку).  
  
3.  Щелкните правой кнопкой мыши **CalendarQuarter** заголовок столбца, а затем щелкните **вставить столбец**.  
  
    Новый столбец с именем **Вычисляемый столбец 1** будет вставлен слева от столбца **Календарный квартал** .  
  
4.  В строке формул над таблицей введите следующую формулу DAX: Автозаполнение помогает вводить полные имена таблиц и столбцов и список доступных функций.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Все строки вычисляемого столбца будут заполнены значениями. Если прокрутить вниз по таблице видно, что строки могут иметь различные значения для этого столбца на основании данных в каждой строке.    
  
5.  Переименовать этот столбец в **MonthCalendar**. 

    ![как newcolumn lesson5](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
MonthCalendar вычисляемый столбец содержит сортируемое имя для месяца.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца DayOfWeek таблицы DimDate  
  
1.  С **DimDate** еще активен, щелкните таблицу **столбца** меню, а затем нажмите **добавить столбец**.  
  
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
  
Вычисляемый столбец ProductSubcategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductSubcategoryName DimProductSubcategory таблицы. Иерархии не могут охватывать более одной таблицы. Создание иерархий позже на занятии 9.  
  
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
  
2.  Создать новый вычисляемый столбец между **SalesAmount** столбца и **TaxAmt** столбца.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Переименуйте столбец в **Маржа**.  
 
      ![как newmargin lesson5](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    Вычисляемый столбец поле используется для анализа маржи для каждой продажи.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 6: Создание мер](../tutorial-tabular-1400/as-lesson-6-create-measures.md).
  
  
  
