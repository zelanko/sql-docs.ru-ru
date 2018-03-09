---
title: "Analysis Services tutorial занятие 2: получение данных | Документы Microsoft"
description: "Описывает, как для получения и импорта данных в проекте служб Analysis Services."
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 1fd06f563581d42764b5b6f29b3c22d8129f9160
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="get-data"></a>Получение данных

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии использовать **получить данные** для подключения к образцу базы данных AdventureWorksDW, выбора данных, предварительного просмотра и фильтрации и затем импортировать в рабочую область модели.  
  
С помощью получения данных, можно импортировать данные из разнообразных источников. Также можно запросить данные с помощью выражения формул Power Query M или [собственного выражения запроса SQL](../tabular-models/ssas-import-query.md).

> [!NOTE]
> Задачи и изображения в этом учебнике показано подключение к базе данных AdventureWorksDW2014 на локальном сервере. В некоторых случаях базы данных AdventureWorksDW, в хранилище данных SQL Azure могут отображаться различные объекты; Тем не менее они фактически являются одинаковыми.
  
Предполагаемое время выполнения данного занятия: **10 минут.**  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятия 1: Создание нового проекта табличной модели](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Создание подключения  
  
#### <a name="to-create-a-connection-to-the-adventureworksdw-database"></a>Для создания подключения к базе данных AdventureWorksDW  
  
1.  В **обозреватель табличной модели**, щелкните правой кнопкой мыши **источники данных** > **Импорт из источника данных**.  
  
    Будет запущен **получение данных**, которое помогает выполнить соединение с источником данных. Если вы не видите обозревателе табличной модели в **обозревателе решений**, дважды щелкните **Model.bim** чтобы открыть модель в конструкторе. 
    
    ![as-lesson2-getdata](../tutorial-tabular-1400/media/as-lesson2-getdata.png)
  
2.  Получить данные, нажмите кнопку **базы данных** > **базы данных SQL Server** > **Connect**.  
  
3.  В **базы данных SQL Server** диалоговое окно, в **сервера**, введите имя сервера, где установлена базы данных AdventureWorksDW и нажмите кнопку **Connect**.  

4.  При появлении запроса введите учетные данные, необходимо указать учетные данные, которые службы Analysis Services использует для подключения к источнику данных при импорте и обработке данных. В **режим олицетворения**выберите **олицетворить учетную запись**, затем введите учетные данные и нажмите кнопку **Connect**. Рекомендуется использовать учетную запись, в которой срок действия пароля не ограничен.

    ![as-lesson2-account](../tutorial-tabular-1400/media/as-lesson2-account.png)
  
    > [!NOTE]  
    > Использование другой пользовательской учетной записи и пароля Windows обеспечивает наиболее безопасный метод подключения к источнику данных.
  
5.  Выберите в навигаторе **AdventureWorksDW** базы данных, а затем нажмите кнопку **ОК**. Это создает соединение с базой данных. 
  
6.  В навигаторе, установите флажок напротив следующих таблиц: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, и **FactInternetSales**.  

    ![as-lesson2-select-tables](../tutorial-tabular-1400/media/as-lesson2-select-tables.png)
  
Редактор запросов открывается после нажатия кнопки ОК. В следующем разделе выберите только данные, которые требуется импортировать.

  
## <a name="filter-the-table-data"></a>Фильтрация данных таблицы  

Таблицы в образце базы данных AdventureWorksDW имеют данные, которые не требуется включить в модель. Если это возможно, нужно выполнить фильтрацию ненужных данных в целях экономии места в памяти, используемых в модели. Можно отфильтровать некоторые столбцы из таблиц, поэтому их не импорта в базу данных рабочей области или базе данных модели после его развертывания. 
  
#### <a name="to-filter-the-table-data-before-importing"></a>Фильтрация данных таблицы перед импортом  
  
1.  В редакторе запросов выберите **DimCustomer** таблицы. Откроется представление таблицы DimCustomer в источнике данных (в образце базы данных AdventureWorksDW). 
  
2.  Множественный выбор, (Ctrl + щелчок мышью) **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**, а затем щелкните правой кнопкой мыши и выберите команду **удалить столбцы**. 

    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-columns.png)
  
    Поскольку значения для этих столбцов не являются актуальными для анализа интернет-продаж, нет необходимости их импортировать. Удалить ненужные столбцы модели меньшего размера и делает более эффективным.  

    > [!TIP]
    > Если допущена ошибка, можно создать резервную копию, удалив шаг в **ПРИМЕНЕННЫХ ДЕЙСТВИЙ**.   
    
    ![as-lesson2-remove-columns](../tutorial-tabular-1400/media/as-lesson2-remove-step.png)

  
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

Предварительного просмотра и фильтрации ненужных данных, можно импортировать остальные нужные данные. Мастер импортирует данные таблицы вместе со всеми связями между таблицами. Новые таблицы и столбцы создаются в модели, а не импортируется отфильтрованные ранее данные.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>Импорт данных выбранных таблиц и столбцов  
  
1.  Просмотрите выбранные параметры. Если все выглядит правильно, нажмите кнопку **импорта**. Обработка данных диалоговое окно показывает состояние данные, импортированные из вашего источника данных в базу данных рабочей области.
  
    ![as-lesson2-success](../tutorial-tabular-1400/media/as-lesson2-success.png) 
  
2.  Щелкните **Закрыть**.  

  
## <a name="save-your-model-project"></a>Сохранять проект модели  

Важно часто сохранять проект модели.  
  
#### <a name="to-save-the-model-project"></a>Сохранение проекта модели  
  
-   Click **Файл** > **Сохранить все**.  
  
## <a name="whats-next"></a>Дальнейшие действия

[Занятие 3: Пометить как таблицу дат](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md).

  
  
