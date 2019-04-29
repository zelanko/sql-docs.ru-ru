---
title: Урок 9. Создание иерархий | Документация Майкрософт
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da8f3d0fb3f733c5a9307d633025bb67a1a4d8cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017258"
---
# <a name="lesson-9-create-hierarchies"></a>Урок 9. Создание иерархий
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии мы создадим иерархии. Иерархии представляют собой группы столбцов, расположенных по уровням; например иерархия География может иметь подуровни для страны, государства, округа и города. В списке полей клиентского средства создания отчетов иерархии могут отображаться отдельно от других столбцов, что упрощает переход по иерархиям и их включение в отчет для пользователей клиента. Дополнительные сведения см. в разделе [иерархий](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Для создания иерархий используется конструктор моделей в *представление схемы*. Создание иерархий и управление ими не поддерживается в представлении данных.  
  
Предполагаемое время для выполнения этого занятия: **20 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 8. Создание перспектив](../analysis-services/lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Создание иерархий  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Создание иерархии категорий в таблице DimProduct  
  
1.  В конструкторе моделей (представление "Схема"), щелкните правой кнопкой мыши **DimProduct** таблицы > **создать иерархию**. Внизу окна таблицы появится новая иерархия. Переименуйте иерархию **категории**.  
  
2.  Щелкните и перетащите **ProductCategoryName** столбца к новому **категории** иерархии.  
  
3.  В **категории** иерархию, щелкните правой кнопкой мыши **ProductCategoryName** > **Переименовать**, а затем введите **категории**.  
  
    > [!NOTE]  
    > Изменение имени столбца в иерархии не влияет на имя этого столбца в таблице. Столбец в иерархии является просто представлением столбца в таблице.  
  
4.  Щелкните и перетащите **ProductSubcategoryName** столбец **категории** иерархии. Переименуйте его **подкатегории**. 
  
5.  Щелкните правой кнопкой мыши **ModelName** столбец > **добавьте иерархию**, а затем выберите **категории**. Сделайте то же самое **EnglishProductName**. Переименовать эти столбцы в иерархии **модели** и **продукта**.  

    ![как табличные lesson9-категории](../analysis-services/media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Для создания иерархий в таблице DimDate  
  
1.  В **DimDate** таблицы, создайте новую иерархию с именем **календаря**.  
  
3.  Добавьте следующие столбцы по порядку:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  В **DimDate** таблицы, создайте **финансового** иерархии. Включите следующие столбцы:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Наконец, в **DimDate** таблицы, создайте **ProductionCalendar** иерархии. Включите следующие столбцы:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [Занятие 10. Создание секций](../analysis-services/lesson-10-create-partitions.md). 
  
  
