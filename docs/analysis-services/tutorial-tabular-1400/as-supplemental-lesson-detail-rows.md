---
title: 'Analysis Services tutorial дополнительного занятия: строки детализации | Документы Microsoft'
description: Описывает, как создать выражение строки детализации в учебнике служб Analysis Services.
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
ms.openlocfilehash: bd138f17df94b94cbe51869b9e364bbd544509f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="supplemental-lesson---detail-rows"></a>Дополнительного занятия - строки детализации

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

В этом дополнительном занятии редактор DAX используется для определения пользовательского выражения строки детализации. Выражение строки детализации — это свойство измерения, предоставляя дополнительные сведения о результатах статистические меры конечных пользователей. 
  
Предполагаемое время выполнения данного занятия: **10 минут.**  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье дополнительное занятие является частью учебника по табличному моделированию. Перед выполнением задач в этом дополнительном занятии, необходимо завершить все предыдущие занятия или иметь завершенный проект образце модели Интернет-продаж Adventure Works.  
  
## <a name="whats-the-issue"></a>Что такое проблему?

Давайте рассмотрим сведения InternetTotalSales меры, прежде чем добавлять выражение строки детализации.

1.  В SSDT выберите **модель** меню > **анализ в Excel** откройте Excel и создать пустую сводную таблицу.
  
2.  В **полей сводной таблицы**, добавьте **InternetTotalSales** мер из таблицы FactInternetSales **значения**, **CalendarYear** из таблицы DimDate **столбцы**, и **EnglishCountryRegionName** для **строк**. Теперь сводной таблицы обеспечивает сводных результатов от InternetTotalSales меры по области и года. 

    ![как занятия подробности строки-сводной таблицы](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. В сводной таблице дважды щелкните сводное значение для года, а имя области. Здесь мы дважды щелкнули Австралия и 2014 года. Новый лист открывается, содержащая данные, но не полезных данных.

    ![как занятия подробности строки-сводной таблицы](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
Что мы хотим видеть здесь является таблицей, содержащей столбцы и строки данных, которые влияют на результат статистической обработки мер InternetTotalSales. Чтобы сделать это, можно добавить выражение строки детализации как свойство меры.

## <a name="add-a-detail-rows-expression"></a>Добавьте выражение строк детализации

#### <a name="to-create-a-detail-rows-expression"></a>Чтобы создать выражение строк детализации 
  
1. В сетку мер таблицы FactInternetSales, щелкните **InternetTotalSales** мер. 

2. В **свойства** > **выражение строки детализации**, нажмите кнопку редактора, чтобы открыть редактор DAX.

    ![как занятия подробности строки эллипса](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

3. В редакторе DAX введите следующее выражение:

    ```
    SELECTCOLUMNS(
    FactInternetSales,
    "Sales Order Number", FactInternetSales[SalesOrderNumber],
    "Customer First Name", RELATED(DimCustomer[FirstName]),
    "Customer Last Name", RELATED(DimCustomer[LastName]),
    "City", RELATED(DimGeography[City]),
    "Order Date", FactInternetSales[OrderDate],
    "Internet Total Sales", [InternetTotalSales]
    )

    ```

    Это выражение указывает имена столбцов и мер из таблицы FactInternetSales и связанные таблицы результатов при двойном щелчке результат статистической обработки в сводной таблице или отчете.

4. В Excel удалить лист, созданной на шаге 3, а затем дважды щелкните это статистическое выражение. На этот раз со свойством выражение строки детализации, определенные для меры, новый лист открывается с гораздо более полезными данными.

    ![как занятия подробности строки detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. Повторное развертывание модели.

  
## <a name="see-also"></a>См. также:  

[Функции SELECTCOLUMNS (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[Дополнительный урок. Динамическая безопасность](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Дополнительный урок. Неоднородные иерархии](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
