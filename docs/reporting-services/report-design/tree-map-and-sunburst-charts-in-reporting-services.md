---
title: "Диаграмма \"дерево\" и \"солнечные лучи\" диаграмм в SQL Server Reporting Services | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/31/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12307c8f-bca7-4d21-8ad5-0c07d819865b
caps.latest.revision: 17
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 5e15fa8674a09821becd437e78cfb0bb472e3bc8
ms.openlocfilehash: 50224e926c08951887a6423ab1c95eb7ac23a944
ms.contentlocale: ru-ru
ms.lasthandoff: 10/30/2017

---
# <a name="treemap-and-sunburst-charts-in-reporting-services"></a>Диаграмма "дерево" и "солнечные лучи" диаграмм в службах Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] визуализации диаграмма "дерево" и "солнечные лучи" прекрасно подходят для визуального представления иерархических данных. В этой статье приведен обзор способов добавления диаграммы диаграмма "дерево" или "солнечные лучи" [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчета. Статья также включает пример запроса AdventureWorks, помогут вам приступить к работе.  
  
##  <a name="bkmk_treemap_chart"></a>Диаграмма, диаграмма "дерево"  

Диаграммы диаграмма "дерево" делит область диаграммы на прямоугольники, представляющие разные уровни и относительные размеры иерархии данных. Эта схема аналогична ветвям дерева, начинающимся от ствола и разделяющимся на ветви меньшего и меньшего размера. Каждый прямоугольник разбивается на более мелкие прямоугольники, представляющие следующий уровень в иерархии. Прямоугольники диаграмма верхнего уровня дерева упорядочены самый большой прямоугольник в левом верхнем углу диаграммы, чтобы наименьшего прямоугольника в правом нижнем углу.  В прямоугольнике следующий уровень, помимо прочего, упорядочивается в виде прямоугольников от левого верхнего угла до правого нижнего угла.  

Например на следующем рисунке диаграмма образца, Юго-Запад Территория является наибольшим и Германия — наименьшей. На юго-западной территории область шоссейных велосипедов больше области горных велосипедов.  
 
![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-treemap-chart-and-set-up-the-sample-adventureworks-data"></a>Вставка диаграммы диаграмма "дерево" и настройка образца данных AdventureWorks  
   
> [!NOTE]
> Перед добавлением диаграммы в отчет создайте источник данных и набора данных.  Образец данных и образец запроса см. в разделе [образец данных AdventureWorks](#bkmk_sample_data).  
  
1.  Щелкните правой кнопкой мыши область конструктора, а затем выберите **вставить** > **диаграммы**. Выберите **древовидной диаграммы** значок.

    ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
   
2.  Измените положение и размер диаграммы. Для использования с образцом данных, с диаграммы шириной в 5 дюймов является достаточно начать.  
  
3.  Добавьте следующие поля из образца данных.  
  
    * **Значения**: LineTotal
    * **Группы категорий** (в следующем порядке):
        1. «Категория»
        2. SubcategoryName
    * **Группы рядов**: TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4.  Чтобы оптимизировать размер страницы для общей схемы диаграммы-дерева, задайте положение условных обозначений внизу.  
  
5.  Чтобы добавить всплывающие подсказки, отображающие подкатегорию и общую сумму, щелкните правой кнопкой мыши **LineTotal**, а затем выберите **свойства ряда**.  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     Задать **подсказка** свойство следующее значение:  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
    Дополнительные сведения см. в разделе [отображение подсказок в ряд &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6.  Измените заголовок диаграммы по умолчанию на **продажи по категориям и по территории**.  
  
7.  Количество отображаемых значений меток зависит от размера шрифта, размера общей области диаграммы и размера определенных прямоугольников. Чтобы видеть больше меток, измените **шрифт метки** свойство **LineTotal** для **10пт** по умолчанию **8pt**.  
  
  
##  <a name="bkmk_sunburst_chart"></a>Диаграмма "солнечные лучи"  
 
На диаграмме "солнечные лучи" Иерархия представляется рядами кругов. Верхним уровнем иерархии является в центре, а более низкие уровни иерархии, отображаемых за пределами центра кольца.  Самый низкий иерархический уровень представляет внешнее кольцо.  
  
![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-set-up-the-sample-adventureworks-data"></a>Вставка диаграммы "солнечные лучи" и настройка образца данных AdventureWorks  
> [!NOTE] 
> Перед добавлением диаграммы в отчет создайте источник данных и набора данных. Образец данных и образец запроса см. в разделе [образец данных AdventureWorks](#bkmk_sample_data).  
  
1.  Щелкните правой кнопкой мыши область конструктора, а затем выберите **вставить** > **диаграммы**. Выберите **"солнечные лучи"** значок.
     
     ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
2.  Измените положение и размер диаграммы. Для использования с образцом данных, с диаграммы шириной в 5 дюймов является достаточно начать.  
  
3.  Добавьте следующие поля из образца данных.  

    * **Значения**: LineTotal
    * **Группы категорий** (в следующем порядке):
        1. «Категория»
        2. SubcategoryName
        3. SalesReasonName
    * **Группы рядов**: TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4.  Чтобы оптимизировать размер страницы для общей схемы диаграммы "солнечные лучи", задайте положение условных обозначений внизу.  
  
5.  Измените заголовок диаграммы по умолчанию на **к категории продаж по территории с причинами покупки**.  
  
6. Чтобы добавить значения групп категорий "солнечные лучи" как метки, задайте свойства label **видимый = true** и **UseValueAsLabel = false**.<br /><br /> Отображаемые значения меток зависят от размера шрифта, размера общей области диаграммы и размера определенных прямоугольников.  Чтобы видеть больше меток, измените **шрифт метки** свойство **LineTotal** для **10пт** по умолчанию **8pt**.

    ![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")
  
7.  Если требуется другой диапазон цветов, измените свойство диаграммы **Palette** .  
    
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
  
##  <a name="bkmk_sample_data"></a>Образец данных AdventureWorks  
 Этот раздел содержит образец запроса и основные шаги для создания источника данных и набора данных в [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]. Если в вашем отчете уже имеется источник данных и набора данных, этот раздел можно пропустить.  
  
 Запрос возвращает подробные данные заказа на продажу AdventureWorks с территорией продаж, категории продукта, Подкатегория продукта и данными о причине покупки.  
  
1.  **Получить данные**.  
  
     Запрос в этом разделе основан на базе данных AdventureWorks, который можно загрузить с сайта GitHub: [AdventureWorks 2016 полной резервной копии](https://github.com/Microsoft/sql-server-samples/releases).  
  
  
2.  **Создать источник данных**.  
  
    1.  В разделе **данные отчета**, щелкните правой кнопкой мыши **источники данных**, а затем выберите **добавить источник данных**.  
  
    2.  Установите флажок **Использовать соединение, внедренное в отчет**.  
  
    3.  Выберите тип подключения **Microsoft SQL Server**.  
  
    4.  Введите строку подключения к серверу и базе данных. Например:  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2016  
        ```  
  
    5.  Чтобы проверить соединение, выберите **проверить подключение** и затем выберите **ОК**.  
  
     Дополнительные сведения о создании источника данных см. в разделе [добавить и проверить подключение данных &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3.  **Создать набор данных**.  
  
    1. В разделе **данные отчета**, щелкните правой кнопкой мыши **наборы данных**и выберите **добавьте набор данных**.  
  
    2. Установите флажок **Использовать набор данных, внедренный в отчет**.  
  
    3. Выберите источник данных, созданный вами.  
  
    4. Выберите **текст** запрос типа, а затем скопируйте и вставьте следующий запрос в **запроса** текстовое поле:  
  
        ```  
        SELECT    Sales.SalesOrderHeader.SalesOrderID, Sales.SalesOrderHeader.OrderDate, Sales.SalesOrderDetail.SalesOrderDetailID, Sales.SalesOrderDetail.ProductID, Sales.SalesOrderDetail.LineTotal,   
                                 Sales.SalesOrderDetail.UnitPrice, Sales.SalesOrderDetail.OrderQty, Production.Product.Name, Production.Product.ProductNumber, Sales.SalesTerritory.TerritoryID, lower(Sales.SalesTerritory.Name) AS TerritoryName,   
                                 Production.ProductSubcategory.Name AS SubcategoryName, Production.ProductCategory.Name AS CategoryName, Sales.SalesReason.SalesReasonID, Sales.SalesReason.Name AS SalesReasonName  
        FROM            Sales.SalesOrderDetail INNER JOIN  
                                 Sales.SalesOrderHeader ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID INNER JOIN  
                                 Production.Product ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID INNER JOIN  
                                 Sales.SalesTerritory ON Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND   
                                 Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID INNER JOIN  
                                 Production.ProductSubcategory ON Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID INNER JOIN  
                                 Production.ProductCategory ON Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID INNER JOIN  
                                 Sales.SalesOrderHeaderSalesReason ON Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID INNER JOIN  
                                 Sales.SalesReason ON Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID  
        ```  
  
    5. Нажмите кнопку **ОК**.  
  
     Дополнительные сведения о создании набора данных см. в разделе [создать общий набор данных или внедренный набор данных &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>См. также:  
* [Общий конструктор наборов данных &#40; Построитель отчетов &#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
* [Отображение всплывающих подсказок для ряда &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)
* [Учебник: Древовидные диаграммы в Power BI](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)
* [Диаграмма "дерево". Приложения визуализации данных Microsoft Research для Office](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
<br>  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]


