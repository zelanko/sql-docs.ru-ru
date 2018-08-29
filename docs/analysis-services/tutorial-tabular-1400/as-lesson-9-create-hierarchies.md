---
title: 'Analysis Services занятие для учебника по 9: создание иерархий | Документация Майкрософт'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
ms.openlocfilehash: 0261da590a30e077db8332aca35ed32dcc5656c6
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43071817"
---
# <a name="create-hierarchies"></a>Создание иерархий

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии мы создадим иерархии. Иерархии представляют собой группы столбцов, упорядоченных по уровням. Например иерархия География может иметь подуровни для страны, состояние, района и города. В списке полей клиентского средства создания отчетов иерархии могут отображаться отдельно от других столбцов, что упрощает переход по иерархиям и их включение в отчет для пользователей клиента. Дополнительные сведения см. в разделе [иерархий](../tabular-models/hierarchies-ssas-tabular.md)
  
Чтобы создать иерархии, используйте конструктор моделей в *представление схемы*. Создание иерархий и управление ими не поддерживается в представлении данных.  
  
Предполагаемое время выполнения данного занятия: **20 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

Эта статья входит в учебник по табличному моделированию, который следует изучать в порядке. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [занятии 8: Создание перспектив](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Создание иерархий  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Создание иерархии категорий в таблице DimProduct  
  
1.  В конструкторе моделей (представление "Схема"), щелкните правой кнопкой мыши **DimProduct** таблицы > **создать иерархию**. Внизу окна таблицы появится новая иерархия. Переименуйте иерархию **категории**.  
  
2.  Щелкните и перетащите **ProductCategoryName** столбца к новому **категории** иерархии.  
  
3.  В **категории** иерархию, щелкните правой кнопкой мыши **ProductCategoryName** > **Переименовать**, а затем введите **категории**.  
  
    > [!NOTE]  
    > Изменение имени столбца в иерархии не влияет на имя этого столбца в таблице. Столбец в иерархии является просто представлением столбца в таблице.  
  
4.  Щелкните и перетащите **ProductSubcategoryName** столбец **категории** иерархии. Переименуйте его **подкатегории**. 
  
5.  Щелкните правой кнопкой мыши **ModelName** столбец > **добавьте иерархию**, а затем выберите **категории**. Переименуйте его **модели**.

6.  Наконец, добавьте **EnglishProductName** в иерархию категорий. Переименуйте его **продукта**.  

    ![как lesson9 категории](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Для создания иерархий в таблице DimDate  
  
1.  В **DimDate** таблицы, создайте иерархию с именем **календаря**.  
  
3.  Добавьте следующие столбцы по порядку:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  В **DimDate** таблицы, создайте **финансового** иерархии. Включают следующие столбцы по порядку:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Наконец, в **DimDate** таблицы, создайте **ProductionCalendar** иерархии. Включают следующие столбцы по порядку:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Дальнейшие действия

[Занятие 10: Создание секций](../tutorial-tabular-1400/as-lesson-10-create-partitions.md). 
  
  
