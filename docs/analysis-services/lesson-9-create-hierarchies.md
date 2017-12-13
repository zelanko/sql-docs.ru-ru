---
title: "Занятие 10: Создание иерархий | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
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
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d154519f39c17d1bdee4cf2a96ddb18f96ac3444
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-9-create-hierarchies"></a>Занятие 9. Создание иерархий
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим иерархии. Иерархии представляют собой группы столбцов, расположенных по уровням; например иерархия География может иметь подуровни для страны, государства, округа и города. В списке полей клиентского средства создания отчетов иерархии могут отображаться отдельно от других столбцов, что упрощает переход по иерархиям и их включение в отчет для пользователей клиента. Дополнительные сведения см. в разделе [иерархий](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Для создания иерархий, будет использоваться в конструкторе моделей *представление диаграммы*. Создание иерархий и управление ими в представлении данных не поддерживается.  
  
Предполагаемое время выполнения данного занятия: **20 минут**  
  
## <a name="prerequisites"></a>Предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 8: Создание перспектив](../analysis-services/lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Создание иерархий  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Чтобы создать иерархию категорий в таблице DimProduct  
  
1.  Щелкните правой кнопкой мыши в конструкторе моделей (представление диаграммы) **DimProduct** таблицы > **создать иерархию**. Внизу окна таблицы появится новая иерархия. Переименуйте иерархию **категории**.  
  
2.  Щелкните и перетащите **ProductCategoryName** столбца к новому **категории** иерархии.  
  
3.  В **категории** иерархии, щелкните правой кнопкой мыши **ProductCategoryName** > **переименование**, а затем введите **категории**.  
  
    > [!NOTE]  
    > Изменение имени столбца в иерархии не влияет на имя этого столбца в таблице. Столбец в иерархии является просто представлением столбца в таблице.  
  
4.  Щелкните и перетащите **ProductSubcategoryName** столбец **категории** иерархии. Переименуйте ее **подкатегории**. 
  
5.  Щелкните правой кнопкой мыши **ModelName** столбца > **добавить в иерархию**, а затем выберите **категории**. Сделайте то же самое **EnglishProductName**. Переименовать эти столбцы в иерархии **модель** и **продукта**.  

    ![как табличные lesson9-категории](../analysis-services/media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Для создания иерархий таблицы DimDate  
  
1.  В **DimDate** таблица, создать новую иерархию с именем **календаря**.  
  
3.  Добавьте следующие столбцы по порядку:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  В **DimDate** , куда вводится **финансовом** иерархии. Включает следующие столбцы:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Наконец, в **DimDate** , куда вводится **ProductionCalendar** иерархии. Включает следующие столбцы:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятии 10: создание секций](../analysis-services/lesson-10-create-partitions.md). 
  
  
