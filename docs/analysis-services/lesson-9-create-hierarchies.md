---
title: 'Занятие 10: Создание иерархий | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6241b60197b783710142c4fd2a2b9ebbf3486b30
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
  
