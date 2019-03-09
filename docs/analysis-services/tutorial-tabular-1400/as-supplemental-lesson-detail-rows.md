---
title: 'Analysis Services дополнительное занятие для учебника по: Строки детализации | Документация Майкрософт'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 20f5f32d4cca8b69d94410296e3653a92a1d6d46
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685249"
---
# <a name="supplemental-lesson---detail-rows"></a>Дополнительный урок. Строки детализации

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

В этом дополнительном занятии вы редактор DAX для определения пользовательского выражения строк детализации. Выражение строк детализации — это свойство на основе меры, предоставляющее конечным пользователям Дополнительные сведения об агрегированных результатах для меры. 
  
Предполагаемое время выполнения данного занятия: **10 минут**  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье дополнительное занятие входит в учебник по табличному моделированию. Перед выполнением задач в этом дополнительном занятии, необходимо завершить все предыдущие занятия или иметь завершенный проект образца модели Adventure Works Internet Sales.  
  
## <a name="whats-the-issue"></a>В чем заключается проблема?

Давайте взглянем на сведения о мере internettotalsales, прежде чем добавлять выражение строк детализации.

1.  В SSDT откройте **модели** меню > **анализ в Excel** открыть Excel и создать пустую сводную таблицу.
  
2.  В **поля сводной таблицы**, добавьте **InternetTotalSales** мер из таблицы FactInternetSales **значения**, **CalendarYear** из таблицы DimDate **столбцы**, и **EnglishCountryRegionName** для **строк**. Теперь Сводная таблица предоставляет агрегированные результаты из меры internettotalsales по регионам и годам. 

    ![как занятие подробно строк — сводной таблицы](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. В сводной таблице дважды щелкните агрегированное значение для года и имени региона. Здесь мы выбрали значение для Австралии за 2014 год. Открывается новый лист, содержащий данные, но не полезных данных.

    ![как занятие подробно строк — сводной таблицы](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
Что мы хотим см. в разделе ниже приведена таблица со столбцами и строками данных, в которой есть доступ к агрегированному результату нашей меры InternetTotalSales. Чтобы сделать это, можно добавить выражение строк детализации в качестве свойства меры.

## <a name="add-a-detail-rows-expression"></a>Добавить выражение строк детализации

#### <a name="to-create-a-detail-rows-expression"></a>Чтобы создать выражение строк детализации 
  
1. Щелкните в сетке мер таблицы FactInternetSales **InternetTotalSales** мер. 

2. В **свойства** > **выражение строк детализации**, нажмите кнопку редактора, чтобы открыть редактор DAX.

    ![как занятие подробно строк — эллипс](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

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

    Это выражение указывает имена, столбцы, и результаты мер из таблицы FactInternetSales и связанных таблиц возвращаются в том случае, когда пользователь дважды щелкает агрегированный результат в сводной таблице или отчете.

4. Вернитесь в Excel удалите лист, созданный на шаге 3, а затем дважды щелкните агрегированное значение. На этот раз с помощью определенного свойства выражение строк детализации для меры, открывается новый лист, содержащий гораздо больше полезных данных.

    ![как занятие подробно строк detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. Разверните модель заново.

  
## <a name="see-also"></a>См. также  

[Функция SELECTCOLUMNS (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[Дополнительный урок. Динамическая безопасность](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Дополнительный урок. Неоднородные иерархии](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
