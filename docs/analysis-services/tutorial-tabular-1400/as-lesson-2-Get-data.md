---
title: 'Analysis Services занятие для учебника по 2: получение данных | Документация Майкрософт'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9adeebfbd3c49761adb816a7d28472a61ffca5cc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007205"
---
# <a name="get-data"></a>Получение данных

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии вы использовать **получить данные** для подключения к базе данных AdventureWorksDW, выбора данных, предварительного просмотра и фильтрации и затем импортировать в рабочую область модели.  
  
С помощью функции получения данных, можно импортировать данные из самых разнообразных источников. Также можно запросить данные с помощью выражения формулы Power Query M или [собственные выражения запроса SQL](../tabular-models/ssas-import-query.md).

> [!NOTE]
> Задачи и образов в этом руководстве показано, подключение к базе данных AdventureWorksDW2014 на локальном сервере. В некоторых случаях к базе данных AdventureWorksDW на хранилище данных SQL Azure могут отображаться различные объекты; Тем не менее они по сути одинаковые.
  
Предполагаемое время выполнения данного занятия: **10 минут.**  
  
## <a name="prerequisites"></a>предварительные требования  

Эта статья входит в учебник по табличному моделированию, который следует изучать в порядке. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [занятии 1: Создание нового проекта табличной модели](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Создание подключения  
  
#### <a name="to-create-a-connection-to-the-adventureworksdw-database"></a>Чтобы создать подключение к базе данных AdventureWorksDW  
  
1.  В **обозреватель табличных моделей**, щелкните правой кнопкой мыши **источников данных** > **Импорт из источника данных**.  
  
    Это откроет **получить данные**, который описывается подключение к источнику данных. Если вы не видите обозреватель табличных моделей в **обозревателе решений**, дважды щелкните **Model.bim** для открытия модели в конструкторе. 
    
    ![как getdata занятие 2](../tutorial-tabular-1400/media/as-lesson2-getdata.png)
  
2.  Получить данные, нажмите кнопку **базы данных** > **базы данных SQL Server** > **Connect**.  
  
3.  В **базы данных SQL Server** диалоговое окно, в **Server**, введите имя сервера, на котором установлена база данных AdventureWorksDW и нажмите кнопку **Connect**.  

4.  При появлении запроса на ввод учетных данных, необходимо указать учетные данные, используемые службами Analysis Services для подключения к источнику данных при импорте и обработке данных. В **режим олицетворения**выберите **олицетворить учетную запись**, затем введите учетные данные и нажмите кнопку **Connect**. Рекомендуется использовать учетную запись, в котором не истечет срок действия пароля.

    ![— занятие 2-учетную запись от имени](../tutorial-tabular-1400/media/as-lesson2-account.png)
  
    > [!NOTE]  
    > Использование другой пользовательской учетной записи и пароля Windows обеспечивает наиболее безопасный метод подключения к источнику данных.
  
5.  В навигаторе выберите **AdventureWorksDW** базы данных, а затем нажмите кнопку **ОК**. Вы создали подключение к базе данных. 
  
6.  В навигаторе установите флажок напротив следующих таблиц: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**,  **DimProductCategory**, **DimProductSubcategory**, и **FactInternetSales**.  

    ![как-занятие 2 выберите tables](../tutorial-tabular-1400/media/as-lesson2-select-tables.png)
  
После нажатия кнопки OK откроется редактор запросов. В следующем разделе выберите только данные, которые требуется импортировать.

  
## <a name="filter-the-table-data"></a>Фильтрация данных таблицы  

Таблицы в образце базы данных AdventureWorksDW содержат данные, которые не обязательно включать в модель. По возможности нужно отфильтровать ненужные данные для экономии места в памяти, используемого моделью. Можно отфильтровать некоторые столбцы из таблиц, они не импортировались в базе данных рабочей области или базе данных модели после его развертывания. 
  
#### <a name="to-filter-the-table-data-before-importing"></a>Чтобы отфильтровать данные таблицы перед импортом  
  
1.  В редакторе запросов выберите **DimCustomer** таблицы. Откроется представление таблицы DimCustomer в источнике данных (в образце базы данных AdventureWorksDW). 
  
2.  Множественный выбор (Ctrl + щелчок) **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**, затем Щелкните правой кнопкой мыши, а затем нажмите кнопку **удалить столбцы**. 

    ![как — занятие 2 remove столбцы](../tutorial-tabular-1400/media/as-lesson2-remove-columns.png)
  
    Поскольку значения для этих столбцов не являются актуальными для анализа интернет-продаж, нет необходимости их импортировать. Исключение ненужных столбцов модель становится компактнее и эффективнее.  

    > [!TIP]
    > Если вы сделаете ошибку, можно выполнять резервное копирование, удалив шаг в **ПРИМЕНЕННЫХ ДЕЙСТВИЙ**.   
    
    ![как — занятие 2 remove столбцы](../tutorial-tabular-1400/media/as-lesson2-remove-step.png)

  
4.  Отфильтруйте оставшиеся таблицы, удалив следующие столбцы в каждой таблице:  
    
    **DimDate**
    
      |Столбец|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |Столбец|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |Столбец|  
      |-----------|  
      |**SpanishProductName**|  
      |**FrenchProductName**|  
      |**FrenchDescription**|  
      |**ChineseDescription**|  
      |**ArabicDescription**|  
      |**HebrewDescription**|  
      |**ThaiDescription**|  
      |**GermanDescription**|  
      |**JapaneseDescription**|  
      |**TurkishDescription**|  
  
    **DimProductCategory**
  
      |Столбец|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |Столбец|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      Столбцы не удалены.
  
## <a name="Import"></a>Import the selected tables and column data  

Теперь, когда вы предварительного просмотра и фильтрации ненужных данных, можно импортировать оставшиеся данные, которые требуется. Мастер импортирует данные таблицы вместе со всеми связями между таблицами. Новые таблицы и столбцы создаются в модели и отфильтрованные данные не импортируются.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>Импорт данных выбранных таблиц и столбцов  
  
1.  Просмотрите выбранные параметры. Если все выглядит правильно, нажмите кнопку **импорта**. В диалоговом окне обработки данных отображаются состояние данных, импортируемых из источника данных в базу данных рабочей области.
  
    ![как — занятие 2-успешное завершение](../tutorial-tabular-1400/media/as-lesson2-success.png) 
  
2.  Щелкните **Закрыть**.  

  
## <a name="save-your-model-project"></a>Сохранять проект модели  

Очень важно часто сохранять проект модели.  
  
#### <a name="to-save-the-model-project"></a>Сохранение проекта модели  
  
-   Click **Файл** > **Сохранить все**.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 3: Обозначение таблицы дат](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md).

  
  
