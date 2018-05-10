---
title: Диаграммы "дерево" и "солнечные лучи" в SQL Server Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 08/31/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 12307c8f-bca7-4d21-8ad5-0c07d819865b
caps.latest.revision: 17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 152507403574ae4c699a3aa30a2376c0ed6b2af2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="treemap-and-sunburst-charts-in-reporting-services"></a>Диаграммы "дерево" и "солнечные лучи" в Reporting Services
[!INCLUDE[feedback-stackoverflow-msdn-connect-md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]
Визуализации "дерево" и "солнечные лучи" SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] прекрасно подходят для визуального представления иерархических данных. В этой статье описывается добавление диаграммы "дерево" или "солнечные лучи" в отчет [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В ней также приводится пример запроса AdventureWorks, который поможет вам приступить к работе.  
  
##  <a name="bkmk_treemap_chart"></a> Диаграмма "дерево"  

Диаграмма "дерево" делит область диаграммы на прямоугольники, представляющие разные уровни и относительные размеры иерархии данных. Эта схема аналогична ветвям дерева, начинающимся от ствола и разделяющимся на ветви меньшего и меньшего размера. Каждый прямоугольник разбивается на более мелкие прямоугольники, представляющие следующий уровень в иерархии. Прямоугольники верхнего уровня дерева упорядочены так, что самый большой прямоугольник находится в левом верхнем углу диаграммы, а самый маленький — в правом нижнем углу.  В прямоугольнике следующий уровень, помимо прочего, упорядочивается в виде прямоугольников от левого верхнего угла до правого нижнего угла.  

Например, на приведенном ниже рисунке показан пример дерева, на котором юго-западная территория является наибольшей, а Германия — наименьшей. На юго-западной территории область шоссейных велосипедов больше области горных велосипедов.  
 
![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-treemap-chart-and-set-up-the-sample-adventureworks-data"></a>Вставка диаграммы "дерево" и настройка образца данных AdventureWorks  
   
> [!NOTE]
> Перед добавлением диаграммы в отчет создайте источник данных и набор данных.  Образец данных и образец запроса см. в разделе [Образец данных AdventureWorks](#bkmk_sample_data).  
  
1.  Щелкните правой кнопкой мыши область конструктора, а затем выберите **Вставить** > **Диаграмма**. Щелкните значок **Дерево**.

    ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
   
2.  Измените положение и размер диаграммы. Для использования с образцом данных достаточно начать с диаграммы шириной в 12 см.  
  
3.  Добавьте следующие поля из образца данных.  
  
    * **Значения**: LineTotal
    * **Группы категорий** (в следующем порядке):
        1. CategoryName
        2. SubcategoryName
    * **Группы рядов**: TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4.  Чтобы оптимизировать размер страницы для общей схемы диаграммы "дерево", задайте положение условных обозначений внизу.  
  
5.  Чтобы добавить подсказки, в которых указывается подкатегория и общая сумма, щелкните правой кнопкой мыши **LineTotal** и выберите пункт **Свойства рядов**.  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     Задайте для свойства **Tooltip** следующее значение:  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
    Дополнительные сведения см. в статье [Отображение всплывающих подсказок для ряда (построитель отчетов и службы SSRS)](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6.  Измените заголовок диаграммы по умолчанию на **Продажи по категориям и по территории**.  
  
7.  Количество отображаемых значений меток зависит от размера шрифта, размера общей области диаграммы и размера определенных прямоугольников. Чтобы видеть больше меток, измените значение свойства **Шрифт метки** поля **LineTotal** на **10 пунктов** вместо значения по умолчанию **8 пунктов**.  
  
  
##  <a name="bkmk_sunburst_chart"></a> Диаграмма "солнечные лучи"  
 
На диаграмме "солнечные лучи" иерархия представлена рядом кругов. Верхний уровень иерархии находится в центре, а более низкие уровни представлены кольцами вокруг него.  Самый низкий иерархический уровень представляет внешнее кольцо.  
  
![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-set-up-the-sample-adventureworks-data"></a>Вставка диаграммы "солнечные лучи" и настройка образца данных AdventureWorks  
> [!NOTE] 
> Перед добавлением диаграммы в отчет создайте источник данных и набор данных. Образец данных и образец запроса см. в разделе [Образец данных AdventureWorks](#bkmk_sample_data).  
  
1.  Щелкните правой кнопкой мыши область конструктора, а затем выберите **Вставить** > **Диаграмма**. Щелкните значок **Солнечные лучи**.
     
     ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
2.  Измените положение и размер диаграммы. Для использования с образцом данных достаточно начать с диаграммы шириной в 12 см.  
  
3.  Добавьте следующие поля из образца данных.  

    * **Значения**: LineTotal
    * **Группы категорий** (в следующем порядке):
        1. CategoryName
        2. SubcategoryName
        3. SalesReasonName
    * **Группы рядов**: TerritoryName  

    ![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")
  
4.  Чтобы оптимизировать размер страницы для общей схемы диаграммы "солнечные лучи", задайте положение условных обозначений внизу.  
  
5.  Измените заголовок диаграммы по умолчанию на **Продажи по категориям и по территории с причинами покупки**.  
  
6. Чтобы добавить значения групп категорий в диаграмму "солнечные лучи" в виде меток, задайте свойства меток **Visible=true** и **UseValueAsLabel=false**.<br /><br /> Отображаемые значения меток зависят от размера шрифта, размера общей области диаграммы и размера определенных прямоугольников.  Чтобы видеть больше меток, измените значение свойства **Шрифт метки** поля **LineTotal** на **10 пунктов** вместо значения по умолчанию **8 пунктов**.

    ![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")
  
7.  Если требуется другой диапазон цветов, измените свойство диаграммы **Palette** .  
    
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
  
##  <a name="bkmk_sample_data"></a> Образец данных AdventureWorks  
 В этом разделе приводится образец запроса и основные инструкции по созданию источника данных и набора данных в [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]. Если в вашем отчете уже имеются источник данных и набор данных, этот раздел можно пропустить.  
  
 Запрос возвращает подробные данные заказа на продажу AdventureWorks с территорией продажи, категорией продукта, подкатегорией продукта и данными по причине покупки.  
  
1.  **Получение данных**.  
  
     Запрос в этом разделе основан на базе данных AdventureWorks, которую можно скачать на странице [полной резервной копии базы данных AdventureWorks 2016](https://github.com/Microsoft/sql-server-samples/releases) в GitHub.  
  
  
2.  **Создание источника данных**.  
  
    1.  В области **Данные отчета** щелкните правой кнопкой мыши элемент **Источники данных** и выберите команду **Добавить источник данных**.  
  
    2.  Установите флажок **Использовать соединение, внедренное в отчет**.  
  
    3.  В качестве типа соединения выберите **Microsoft SQL Server**.  
  
    4.  Введите строку подключения к серверу и базе данных. Пример:  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2016  
        ```  
  
    5.  Чтобы проверить подключение, нажмите кнопку **Проверить подключение**, а затем кнопку **ОК**.  
  
     Дополнительные сведения о создании источника данных см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3.  **Создание набора данных**.  
  
    1. В области **Данные отчета** щелкните правой кнопкой мыши элемент **Наборы данных** и выберите команду **Добавить набор данных**.  
  
    2. Установите флажок **Использовать набор данных, внедренный в отчет**.  
  
    3. Выберите созданный источник данных.  
  
    4. Выберите тип запроса **Текст**, а затем скопируйте и вставьте следующий запрос в текстовое поле **Запрос**:  
  
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
  
     Дополнительные сведения о создании набора данных см. в разделе [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>См. также раздел  
* [Представление конструктора общих наборов данных (построитель отчетов)](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
* [Отображение всплывающих подсказок для ряда (построитель отчетов и службы SSRS)](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)
* [Учебник. Диаграммы "дерево" в Power BI](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)
* [Диаграмма "дерево". Приложения визуализации данных Microsoft Research для Office](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
<br>  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

