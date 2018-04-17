---
title: 'Занятие учебника Analysis Services 9: создание иерархий | Документы Microsoft'
description: ''
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 6821104370c324bf70c806cec96a7a1e53e7931d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-hierarchies"></a>Создание иерархий

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии необходимо создать иерархии. Иерархии представляют собой группы столбцов, расположенных по уровням. Например иерархия География могут иметь подуровни для страны, состояние, округа и города. В списке полей клиентского средства создания отчетов иерархии могут отображаться отдельно от других столбцов, что упрощает переход по иерархиям и их включение в отчет для пользователей клиента. Дополнительные сведения см. в разделе [иерархий](../tabular-models/hierarchies-ssas-tabular.md)
  
Для создания иерархий, используйте конструктор моделей в *представление диаграммы*. Создание иерархий и управление ими в представлении данных не поддерживается.  
  
Предполагаемое время выполнения данного занятия: **20 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 8: Создание перспектив](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Создание иерархий  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Чтобы создать иерархию категорий в таблице DimProduct  
  
1.  Щелкните правой кнопкой мыши в конструкторе моделей (представление диаграммы) **DimProduct** таблицы > **создать иерархию**. Внизу окна таблицы появится новая иерархия. Переименуйте иерархию **категории**.  
  
2.  Щелкните и перетащите **ProductCategoryName** столбца к новому **категории** иерархии.  
  
3.  В **категории** иерархии, щелкните правой кнопкой мыши **ProductCategoryName** > **переименование**, а затем введите **категории**.  
  
    > [!NOTE]  
    > Изменение имени столбца в иерархии не влияет на имя этого столбца в таблице. Столбец в иерархии является просто представлением столбца в таблице.  
  
4.  Щелкните и перетащите **ProductSubcategoryName** столбец **категории** иерархии. Переименуйте ее **подкатегории**. 
  
5.  Щелкните правой кнопкой мыши **ModelName** столбца > **добавить в иерархию**, а затем выберите **категории**. Переименуйте ее **модели**.

6.  Наконец, добавьте **EnglishProductName** иерархии категорий. Переименуйте ее **продукта**.  

    ![как lesson9 категории](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Для создания иерархий таблицы DimDate  
  
1.  В **DimDate** таблице, создайте иерархию с именем **календаря**.  
  
3.  Добавьте следующие столбцы по порядку:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  В **DimDate** , куда вводится **финансовом** иерархии. Включить следующие столбцы по порядку:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Наконец, в **DimDate** , куда вводится **ProductionCalendar** иерархии. Включить следующие столбцы по порядку:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Дальнейшие действия

[Занятие 10: Создание секций](../tutorial-tabular-1400/as-lesson-10-create-partitions.md). 
  
  
