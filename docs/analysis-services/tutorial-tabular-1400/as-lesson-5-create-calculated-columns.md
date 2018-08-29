---
title: 'Analysis Services занятие для учебника по 5: Создание вычисляемых столбцов | Документация Майкрософт'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58a7f38dbbe7a68668418db4d1bef16e08784a08
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43063863"
---
# <a name="create-calculated-columns"></a>Создание вычисляемых столбцов

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии создается данных в модели путем добавления вычисляемых столбцов. Можно создать вычисляемые столбцы (в качестве пользовательских столбцов) при использовании функции получения данных, с помощью редактора запросов или позднее в модели конструктора так вы и воспользуетесь. Дополнительные сведения см. в разделе [вычисляемых столбцов](../tabular-models/ssas-calculated-columns.md).
  
Пять новых вычисляемых столбцов создаются в трех разных таблицах. Действия немного отличаются для каждой задачи, в том, что существует несколько способов создать столбцы, переименовать их и поместите их в различных местах в таблице.  

Это занятие является также, где сначала с помощью выражений анализа данных (DAX). DAX — это специальный язык, для создания сложные настраиваемые выражения формул для табличных моделей. В этом руководстве используется DAX для создания вычисляемых столбцов, мер и фильтров ролей. Дополнительные сведения см. в разделе [DAX в табличных моделях](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md). 
  
Предполагаемое время выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

Эта статья входит в учебник по табличному моделированию, который следует изучать в порядке. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [занятия 4: Создание связей](../tutorial-tabular-1400/as-lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Создание вычисляемых столбцов  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца MonthCalendar в таблице DimDate  
  
1.  Нажмите кнопку **модели** меню > **представление модели** > **представление данных**.  
  
    Вычисляемые столбцы можно создавать только с помощью конструктора моделей в представлении данных.  
  
2.  В конструкторе моделей щелкните **DimDate** таблицу (вкладку).  
  
3.  Щелкните правой кнопкой мыши **CalendarQuarter** заголовок столбца, а затем щелкните **вставить столбец**.  
  
    Новый столбец с именем **Вычисляемый столбец 1** будет вставлен слева от столбца **Календарный квартал** .  
  
4.  В строке формул над таблицей введите следующую формулу DAX: компонент автозаполнения помогает вводить полные имена столбцов и таблиц и перечисляет функции, которые доступны.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Все строки вычисляемого столбца будут заполнены значениями. Если вы прокрутите страницу вниз по таблице, вы увидите, что строки могут содержать разные значения для этого столбца, на основе данных в каждой строке.    
  
5.  Переименуйте этот столбец в **MonthCalendar**. 

    ![как newcolumn lesson5](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
MonthCalendar вычисляемый столбец содержит поддерживающее сортировку имя для месяца.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Создание вычисляемого столбца DayOfWeek в таблице DimDate  
  
1.  С помощью **DimDate** активна, откройте таблицу **столбец** меню, а затем щелкните **добавить столбец**.  
  
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
  
Вычисляемый столбец ProductSubcategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductSubcategoryName таблицы DimProductSubcategory. Иерархии не могут охватывать более одной таблицы. Вы создадите иерархии позднее в занятии 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Создание вычисляемого столбца ProductCategoryName в таблице DimProduct  
  
1.  С помощью **DimProduct** активна, откройте таблицу **столбец** меню, а затем щелкните **добавить столбец**.  
  
2.  В строке формул введите следующую формулу:  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Переименуйте столбец в **ProductCategoryName**.  
  
Вычисляемый столбец ProductCategoryName используется для создания иерархии в таблице DimProduct, которая включает данные из столбца EnglishProductCategoryName таблицы DimProductCategory. Иерархии не могут охватывать более одной таблицы.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Создание вычисляемого столбца Margin в таблице FactInternetSales  
  
1.  В конструкторе моделей выберите **FactInternetSales** таблицы.  
  
2.  Создать новый вычисляемый столбец между **SalesAmount** столбца и **TaxAmt** столбца.  
  
3.  В строке формул введите следующую формулу:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Переименуйте столбец в **Маржа**.  
 
      ![как newmargin lesson5](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    Вычисляемый столбец Margin используется для анализа маржи для каждой продажи.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 6: Создание мер](../tutorial-tabular-1400/as-lesson-6-create-measures.md).
  
  
  
