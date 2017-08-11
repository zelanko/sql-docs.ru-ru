---
title: "Диаграммы \"дерево\" и \"солнечные лучи\" в Reporting Services | Документация Майкрософт"
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
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e09afe4634c02db6e74413e7c1c10565450b3559
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="tree-map-and-sunburst-charts-in-reporting-services"></a>Диаграммы "дерево" и "солнечные лучи" в Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  Визуализации "дерево" и "солнечные лучи" [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] прекрасно подходят для визуального представления иерархических данных.   В этом разделе описывается добавление диаграммы "дерево" или "солнечные лучи" в отчет [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Кроме того, в раздел включен пример запроса Adventureworks, который поможет вам приступить к работе.  
  
##  <a name="bkmk_treemap_chart"></a> Диаграмма "дерево"  
 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
  
 Диаграмма "дерево" делит область диаграммы на прямоугольники, представляющие разные уровни и относительные размеры иерархии данных. Эта схема аналогична ветвям дерева, начинающимся от ствола и разделяющимся на ветви меньшего и меньшего размера. Каждый прямоугольник разбивается на более мелкие прямоугольники, представляющие следующий уровень в иерархии. Прямоугольники верхнего уровня дерева упорядочены так, что самый большой прямоугольник находится в верхнем левом углу диаграммы, а самый маленький — в правом нижнем углу.  В прямоугольнике следующий уровень, помимо прочего, упорядочивается в виде прямоугольников от левого верхнего угла до правого нижнего угла.  
  
 Например, на следующем рисунке показан пример дерева, на котором юго-западная территория является наибольшей, а Германия — наименьшей. На юго-западной территории область шоссейных велосипедов больше области горных велосипедов.  
  
 ![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-tree-map-chart-and-configure-for-the-sample-adventureworks-data"></a>Вставка диаграммы "дерево" и настройка для образца данных Adventureworks  
 **Примечание.** Перед добавлением диаграммы в отчет создайте источник данных и набор данных.  Образец данных и образец запроса см. в разделе [Образец данных Adventureworks](#bkmk_sample_data) этой статьи.  
  
1.  Щелкните правой кнопкой мыши рабочую область конструирования, выберите команду **Вставить**и щелкните пункт **Диаграмма** .  
  
     Выберите диаграмму "дерево" ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon").  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  Измените положение и размер диаграммы.   Для использования с образцом данных достаточно начать с диаграммы шириной в 5 дюймов.  
  
3.  Добавьте следующие поля из образца данных.  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**Значения:** LineTotal<br /><br /> **Группы категорий:** добавлять в следующем порядке:<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> **Группы рядов:** TerritoryName|  
  
4.  Чтобы оптимизировать размер страницы для общей схемы дерева, задайте положение условных обозначений внизу.  
  
5.  Чтобы добавить всплывающие подсказки, отображающие подкатегорию и общую сумму, щелкните правой кнопкой мыши **LineTotal** и нажмите **Свойства рядов**.  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     Задайте в свойстве **Tooltip** следующее значение:  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
     Дополнительные сведения см. в разделе [Отображение всплывающих подсказок для ряда (построитель отчетов и службы SSRS)](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6.  Измените заголовок диаграммы по умолчанию на "Продажи по категориям и по территории".  
  
7.  Количество отображаемых значений меток зависит от размера шрифта, размера общей области диаграммы и размера определенных прямоугольников.  Чтобы видеть больше меток, измените значение свойства шрифта LineTotal на 8 pt вместо значения по умолчанию 10 pt.  
  
  
##  <a name="bkmk_sunburst_chart"></a> Диаграмма "солнечные лучи"  
 ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
 На диаграмме "солнечные лучи" иерархия представляется рядами кругов, причем наивысший иерархический уровень находится в центре, а более низкие уровни иерархии отображаются в виде колец за центром.  Самый низкий иерархический уровень представляет внешнее кольцо.  
  
 ![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-configure-for-the-sample-adventureworks-data"></a>Вставка диаграммы "солнечные лучи" и настройка для образца данных Adventureworks  
 **Примечание.** Перед добавлением диаграммы в отчет создайте источник данных и набор данных.  Образец данных и образец запроса см. в разделе [Образец данных Adventureworks](#bkmk_sample_data) этой статьи.  
  
1.  Щелкните правой кнопкой мыши рабочую область конструирования, выберите команду **Вставить**и щелкните пункт **Диаграмма** .  
  
     Выберите диаграмму "солнечные лучи" ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon").  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  Измените положение и размер диаграммы.   Для использования с образцом данных достаточно начать с диаграммы шириной в 5 дюймов.  
  
3.  Добавьте следующие поля из образца данных.  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**Значения:** LineTotal<br /><br /> **Группы категорий:** добавлять в следующем порядке:<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> 3) SalesReasonName<br /><br /> **Группы рядов:** TerritoryName|  
  
4.  Чтобы оптимизировать размер страницы для общей схемы диаграммы "солнечные лучи", задайте положение условных обозначений внизу.  
  
5.  Измените заголовок диаграммы по умолчанию на "Продажи по категориям и по территории с причинами покупки".  
  
6.  |||  
    |-|-|  
    |![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")|Чтобы добавить значения групп категорий в диаграмму "солнечные лучи" как метки, установите свойство метки **Visible** =true и свойство метки **UseValueAsLabel**=False.<br /><br /> Отображаемые значения меток зависят от размера шрифта, размера общей области диаграммы и размера определенных прямоугольников.  Чтобы видеть больше меток, измените значение свойства шрифта LineTotal на 8 pt вместо значения по умолчанию 10 pt.|  
  
7.  Если требуется другой диапазон цветов, измените свойство диаграммы **Palette** .  
  
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
  
##  <a name="bkmk_sample_data"></a> Образец данных Adventureworks  
 В этом разделе содержится образец запроса и основные шаги для создания источника данных и набора данных в [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]. Если в вашем отчете уже имеется источник данных и набор данных, этот раздел можно пропустить.  
  
 Запрос возвращает подробные данные заказа на продажу Adventureworks с территорией продажи, категорией продукта, подкатегорией продукта и данными о причине покупки.  
  
1.  **Получение данных:**  
  
     Запрос в этом разделе основан на базе данных Adventureworks, которую можно загрузить на странице  [полной резервной копии базы данных Adventure Works 2014](https://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
     Дополнительные сведения о том, как установить базу данных, см. в документе [How to install Adventure Works 2014 Sample Databases.pdf](https://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
2.  **Создание источника данных:**  
  
    1.  В области **Данные отчета** щелкните правой кнопкой мыши пункт **Источник данных** и выберите команду **Добавить источник данных**.  
  
    2.  Установите флажок **Использовать соединение, внедренное в отчет**.  
  
    3.  Выберите тип подключения **Microsoft SQL Server**.  
  
    4.  Введите строку подключения к вашему серверу и базе данных, например:  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2014  
        ```  
  
    5.  Рекомендуется выполнить проверку с помощью кнопки **Проверить подключение** , а затем нажать кнопку **ОК**.  
  
     Дополнительные сведения о создании источника данных см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3.  **Создание набора данных**  
  
    -   В области **Данные отчета** щелкните правой кнопкой мыши пункт **Наборы данных** и выберите команду **Добавить набор данных**.  
  
    -   Установите флажок **Использовать набор данных, внедренный в отчет**.  
  
    -   Выберите источник данных, созданный на предыдущих шагах.  
  
    -   Выберите тип запроса **Текст** , затем скопируйте и вставьте следующий запрос в текстовое поле **Запрос:** .  
  
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
  
    -   Нажмите кнопку **ОК**.  
  
     Дополнительные сведения о создании набора данных см. в разделе [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>См. также:  
 [Представление конструктора общих наборов данных (построитель отчетов)](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [Отображение всплывающих подсказок для ряда &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)   
 [Учебник. Диаграммы "дерево" в Power BI](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)   
 [Диаграмма "дерево". Приложения визуализации данных Microsoft Research для Office](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]


