---
title: Программирование основных объектов AMO OLAP | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: ad1c970e-c0cb-4687-9563-56ab62c2db5f
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df3206f9bf6bd0548749abf981d6088e9ab85c0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096543"
---
# <a name="programming-amo-olap-basic-objects"></a>Программирование основных объектов AMO OLAP
  Процесс создания сложных объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] является простым и понятным, но требует внимания к деталям. В этом разделе подробно описывается программирование базовых объектов OLAP. Этот раздел состоит из следующих подразделов.  
  
-   [Объекты измерений](#Dim)  
  
-   [Объекты кубов](#Cub)  
  
-   [Объекты MeasureGroup](#MG)  
  
-   [Объекты partition](#Part)  
  
-   [Объекты Aggregation](#AD)  
  
##  <a name="Dim"></a> Объекты измерений  
 Объект <xref:Microsoft.AnalysisServices.Dimension> программируется для администрирования или обработки измерения.  
  
### <a name="creating-dropping-and-finding-a-dimension"></a>Создание, удаление и поиск измерения  
 Для создания объекта <xref:Microsoft.AnalysisServices.Dimension> необходимо выполнить четыре действия.  
  
1.  Создайте объект измерения и заполните основные атрибуты.  
  
     Основными атрибутами являются: «Имя», «Тип измерения», «Режим хранения», «Привязка к источнику данных», «Имя элемента "Все" атрибута» и другие атрибуты измерения.  
  
     Перед созданием измерения необходимо удостоверится, что такое измерение не существует. Если измерение существует, то оно будет удалено и создано повторно.  
  
2.  Создайте атрибуты, определяющие измерение.  
  
     Перед его использованием каждый атрибут необходимо добавить в схему отдельно (метод CreateDataItem приведен в конце образца кода), а затем его можно будет добавить в коллекцию атрибутов измерения.  
  
     Столбцы «Key» и «Name» должны быть определены во всех атрибутах.  
  
     Первичный ключевой атрибут измерения следует определять как AttributeUsage.Key, чтобы было ясно, что этот атрибут является ключом доступа к измерению.  
  
3.  Создайте иерархии, доступ к которым будет получать пользователь для обзора измерения.  
  
     При создании иерархий порядок уровней определяется порядком, в котором сверху вниз создаются уровни. Верхним уровнем является добавленный первым в коллекцию уровней иерархии.  
  
4.  Обновите сервер при помощи метода Update текущего измерения.  
  
 В следующем образце кода создается измерение Product для.  
  
```  
static void CreateProductDimension(Database db, string datasourceName)  
{  
    // Create the Product dimension  
    Dimension dim = db.Dimensions.FindByName("Product");  
    if ( dim != null)  
       dim.Drop();  
    dim = db.Dimensions.Add("Product");  
    dim.Type = DimensionType.Products;  
    dim.UnknownMember = UnknownMemberBehavior.Hidden;  
    dim.AttributeAllMemberName = "All Products";  
    dim.Source = new DataSourceViewBinding(datasourceName);  
    dim.StorageMode = DimensionStorageMode.Molap;  
  
    #region Create attributes  
  
    DimensionAttribute attr;  
  
    attr = dim.Attributes.Add("Product Name");  
    attr.Usage = AttributeUsage.Key;  
    attr.Type = AttributeType.Product;  
    attr.OrderBy = OrderBy.Name;  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductKey"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProduct", "EnglishProductName");  
  
    attr = dim.Attributes.Add("Product Line");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductLine"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductLineName");  
  
    attr = dim.Attributes.Add("Model Name");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ModelName"));  
    attr.AttributeRelationships.Add(new AttributeRelationship("Product Line"));  
    attr.AttributeRelationships.Add(new AttributeRelationship("Subcategory"));  
  
    attr = dim.Attributes.Add("Subcategory");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProductSubcategory", "ProductSubcategoryKey"));  
    attr.KeyColumns[0].NullProcessing = NullProcessing.UnknownMember;  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProductSubcategory", "EnglishProductSubcategoryName");  
    attr.AttributeRelationships.Add(new AttributeRelationship("Category"));  
  
    attr = dim.Attributes.Add("Category");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProductCategory", "ProductCategoryKey"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProductCategory", "EnglishProductCategoryName");  
  
    attr = dim.Attributes.Add("List Price");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ListPrice"));  
    attr.AttributeHierarchyEnabled = false;  
  
    attr = dim.Attributes.Add("Size");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "Size"));  
    attr.AttributeHierarchyEnabled = false;  
  
    attr = dim.Attributes.Add("Weight");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "Weight"));  
    attr.AttributeHierarchyEnabled = false;  
  
    #endregion  
  
    #region Create hierarchies  
  
    Hierarchy hier;  
  
    hier = dim.Hierarchies.Add("Product Model Categories");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Category").SourceAttributeID = "Category";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Subcategory";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Model Name";  
  
    hier = dim.Hierarchies.Add("Product Categories");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Category").SourceAttributeID = "Category";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Subcategory";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Product Name";  
  
    hier = dim.Hierarchies.Add("Product Model Lines");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Product Line";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Model Name";  
  
    #endregion  
  
    dim.Update();  
}  
  
static DataItem CreateDataItem(DataSourceView dsv, string tableName, string columnName)  
{  
    DataTable dataTable = ((DataSourceView)dsv).Schema.Tables[tableName];  
    DataColumn dataColumn = dataTable.Columns[columnName];  
    return new DataItem(tableName, columnName,  
        OleDbTypeConverter.GetRestrictedOleDbType(dataColumn.DataType));  
}  
  
```  
  
### <a name="processing-a-dimension"></a>Обработка измерения  
 Процесс обработки измерения сводится к использованию метода Process объекта <xref:Microsoft.AnalysisServices.Dimension>.  
  
 Обработка измерения может затронуть все кубы, использующие это измерение. Дополнительные сведения о параметрах обработки см. в разделе [обработки объектов &#40;XMLA&#41; ](../../xmla/xml-elements-objects.md) и [многомерной модели обработки объекта](../processing-a-multidimensional-model-analysis-services.md).  
  
 В следующем коде выполняется добавочное обновление во всех измерениях указанной базы данных:  
  
```  
static void UpdateAllDimensions(Database db)  
{  
    foreach (Dimension dim in db.Dimensions)  
        dim.Process(ProcessType.ProcessUpdate);  
}  
```  
  
##  <a name="Cub"></a> Объекты куба  
 В целях администрирования и обработки куба программируется объект <xref:Microsoft.AnalysisServices.Cube>.  
  
### <a name="creating-dropping-and-finding-a-cube"></a>Создание, удаление и поиск куба  
 Управление кубами осуществляется так же, как управление измерениями. Для создания объекта <xref:Microsoft.AnalysisServices.Cube> необходимо выполнить четыре действия.  
  
1.  Создайте объект куба и заполните основные атрибуты.  
  
     Основными атрибутами являются «Имя», «Режим хранения», «Привязка к источнику данных», «Мера по умолчанию» и другие атрибуты куба.  
  
     Перед созданием куба следует удостовериться, что такой куб не существует. В данном образце, если куб существует, то будет удален, а затем снова создан.  
  
2.  Добавление измерений куба.  
  
     Измерения добавляются в текущую коллекцию измерений куба из базы данных; измерения в кубе представляют собой ссылки на коллекцию измерений в базе данных. Каждое измерение необходимо сопоставлять с кубом отдельно. В данном образце измерения сопоставляются с указанием внутреннего идентификатора измерения в базе данных, имени измерения в кубе и идентификатора для этого именованного измерения в кубе.  
  
     Обратите внимание, что в образце кода измерение «Date» добавляется три раза и при каждом добавлении используется другое имя измерения куба: «Date», «Ship Date», «Delivery Date». Эти измерения называются «ролевыми». Базовое измерение одно («Date»), однако в таблице фактов измерение используется в других «ролях» («Order Date», «Ship Date», «Delivery Date») — описание определения ролевых измерений см. в разделе «Создание, удаление и поиск MeasureGroup» далее в этом документе.  
  
3.  Создайте группы мер, доступ к которым будет получать пользователь, чтобы просматривать данные куба.  
  
     Создание группы мер описывается в разделе «Создание, удаление и поиск группы мер» ниже в этом документе. В этом образце в качестве оболочки для процесса создания группы мер применяются разные методы, по одному на каждую группу мер.  
  
4.  Обновите сервер при помощи метода Update текущего куба.  
  
     Метод обновления используется с параметром обновления ExpandFull, что позволяет гарантировать полное обновление всех объектов на сервере.  
  
 В следующем образце кода создаются части куба Adventure Works. В этом образце кода не создаются все измерения или группы мер, включенные в образец проекта служб Adventure Works Analysis Services.  
  
```  
static void CreateAdventureWorksCube(Database db, string datasourceName)  
{  
    // Create the Adventure Works cube  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    if ( cube != null)  
       cube.Drop();  
    db.Cubes.Add("Adventure Works");  
    cube.DefaultMeasure = "[Reseller Sales Amount]";  
    cube.Source = new DataSourceViewBinding(datasourceName);  
    cube.StorageMode = StorageMode.Molap;  
  
    #region Create cube dimensions  
  
    Dimension dim;  
  
    dim = db.Dimensions.GetByName("Date");  
    cube.Dimensions.Add(dim.ID, "Date", "Order Date Key - Dim Time");  
    cube.Dimensions.Add(dim.ID, "Ship Date",  
        "Ship Date Key - Dim Time");  
    cube.Dimensions.Add(dim.ID, "Delivery Date",  
        "Delivery Date Key - Dim Time");  
  
    dim = db.Dimensions.GetByName("Customer");  
    cube.Dimensions.Add(dim.ID);  
  
    dim = db.Dimensions.GetByName("Reseller");  
    cube.Dimensions.Add(dim.ID);  
    #endregion  
  
    #region Create measure groups  
  
    CreateSalesReasonsMeasureGroup(cube);  
    CreateInternetSalesMeasureGroup(cube);  
    CreateResellerSalesMeasureGroup(cube);  
    CreateCustomersMeasureGroup(cube);  
    CreateCurrencyRatesMeasureGroup(cube);  
  
    #endregion  
  
    cube.Update(UpdateOptions.ExpandFull);  
}  
```  
  
### <a name="processing-a-cube"></a>Обработка куба  
 Процесс обработки куба сводится к использованию метода Process объекта <xref:Microsoft.AnalysisServices.Cube>. При обработке куба обрабатываются все группы мер в этом кубе, а также все секции в группах мер. В кубе единственными объектами, которые можно обработать, являются секции; группы мер с точки зрения обработки представляют собой всего лишь контейнеры секций. Выбранный для куба тип обработки распространяется и на его секции. Обработка куба и группы мер по существу сводится к обработке измерений и секций.  
  
 Дополнительные сведения о параметрах обработки см. в разделе [обработки объектов &#40;XMLA&#41;](../../xmla/xml-elements-objects.md), и [многомерной модели обработки объекта](../processing-a-multidimensional-model-analysis-services.md).  
  
 В следующем коде выполняется полная обработка всех кубов в указанной базе данных:  
  
```  
foreach (Cube cube in db.Cubes)  
             cube.Process(ProcessType.ProcessFull);  
     }  
```  
  
##  <a name="MG"></a> Объекты MeasureGroup  
 В целях администрирования или обработки группы мер программируется объект <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
### <a name="creating-dropping-and-finding-a-measuregroup"></a>Создание, удаление и поиск группы мер  
 Управление группами мер осуществляется так же, как управление измерениями и кубами. Создание объекта <xref:Microsoft.AnalysisServices.MeasureGroup> выполняется путем следующих действий.  
  
1.  Создайте объект группы мер и заполните основные атрибуты.  
  
     Основными атрибутами являются «Имя», «Режим хранения», «Режим обработки», «Мера по умолчанию» и другие атрибуты группы мер.  
  
     Перед созданием группы мер проверьте, что такая группа мер не существует. В приведенном ниже образце кода предусмотрено, что если группа мер существует, то будет удалена и создана повторно.  
  
2.  Создайте меры группы мер. Каждой создаваемой группе мер назначаются следующие атрибуты: имя, статистическая функция, исходный столбец, строка форматирования. Могут быть назначены и другие атрибуты. Обратите внимание, что в приведенном ниже образце кода метод CreateDataItem добавляет столбец в схему.  
  
3.  Добавление измерений группы мер.  
  
4.  Измерения добавляются в текущую коллекцию измерений группы мер из коллекции измерений родительского куба. Как только измерение будет включено в коллекцию измерений группы мер, ключевой столбец из таблицы фактов можно будет сопоставить с этим измерением, чтобы данную группу мер можно было просматривать через это измерение.  
  
     В приведенном далее образце кода см. строки под заголовком «Mapping dimension and key column from fact table». Ролевые измерения реализуются путем связывания разных суррогатных ключей с одним измерением под разными именами. С каждым из ролевых измерений («Date», «Ship Date», «Delivery Date») связывается отдельный суррогатный ключ (OrderDateKey, ShipDateKey, DueDateKey). Все ключи берутся из таблицы фактов FactInternetSales.  
  
5.  Добавление спроектированных секций группы мер.  
  
     В приведенном далее образце кода в качестве оболочки для процесса создания секции применяется один метод.  
  
6.  Обновите сервер при помощи метода Update текущей группы мер.  
  
     В приведенном далее образце кода все группы мер обновляются при обновлении куба.  
  
 В следующем образце кода создастся группа мер InternetSales образца проекта служб Adventure Works Analysis Services.  
  
```  
static void CreateInternetSalesMeasureGroup(Cube cube)  
{  
    // Create the Internet Sales measure group  
    Database db = cube.Parent;  
    MeasureGroup mg = cube.MeasureGroups.FindByName("Internet Sales");  
    if ( mg != null)  
       mg.Drop();  
    mg = cube.MeasureGroups.Add("Internet Sales");  
    mg.StorageMode = StorageMode.Molap;  
    mg.ProcessingMode = ProcessingMode.LazyAggregations;  
    mg.Type = MeasureGroupType.Sales;  
  
    #region Create measures  
  
    Measure meas;  
  
    meas = mg.Measures.Add("Internet Sales Amount");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "Currency";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesAmount");  
  
    meas = mg.Measures.Add("Internet Order Quantity");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "#,#";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "OrderQuantity");  
  
    meas = mg.Measures.Add("Internet Unit Price");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "Currency";  
    meas.Visible = false;  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "UnitPrice");  
  
    meas = mg.Measures.Add("Internet Total Product Cost");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    //meas.MeasureExpression = "[Internet Total Product Cost] * [Average Rate]";  
    meas.FormatString = "Currency";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "TotalProductCost");  
  
    meas = mg.Measures.Add("Internet Order Count");  
    meas.AggregateFunction = AggregationFunction.Count;  
    meas.FormatString = "#,#";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ProductKey");  
  
    #endregion  
  
    #region Create measure group dimensions  
  
    CubeDimension cubeDim;  
    RegularMeasureGroupDimension regMgDim;  
    ManyToManyMeasureGroupDimension mmMgDim;  
    MeasureGroupAttribute mgAttr;  
  
    //   Mapping dimension and key column from fact table  
    //      > select dimension and add it to the measure group  
    cubeDim = cube.Dimensions.GetByName("Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
  
    //      > add key column from dimension and map it with   
    //        the surrogate key in the fact table  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);   // this is dimension key column  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "OrderDateKey"));   // this surrogate key in fact table  
  
    cubeDim = cube.Dimensions.GetByName("Ship Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ShipDateKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Delivery Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "DueDateKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Customer");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Full Name").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "CustomerKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Product");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Product Name").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ProductKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Source Currency");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Currency").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "CurrencyKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Sales Reason");  
    mmMgDim = new ManyToManyMeasureGroupDimension();  
    mmMgDim.CubeDimensionID = cubeDim.ID;  
    mmMgDim.MeasureGroupID = cube.MeasureGroups.GetByName("Sales Reasons").ID;  
    mg.Dimensions.Add(mmMgDim);  
  
    cubeDim = cube.Dimensions.GetByName("Internet Sales Order Details");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Sales Order Key").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesOrderNumber"));  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesOrderLineNumber"));  
  
    #endregion  
  
    #region Create partitions  
  
    CreateInternetSalesMeasureGroupPartitions( mg)  
  
    #endregion  
}  
```  
  
### <a name="processing-a-measure-group"></a>Обработка группы мер  
 Процесс обработки группы мер сводится к использованию метода Process объекта <xref:Microsoft.AnalysisServices.MeasureGroup>. При отработке группы мер будут также обработаны и все секции, принадлежащие к ней. Внутри группы мер ее обработка сводится к обработке измерений и секций. См. раздел [Обработка секции](#ProcPart) в этом документе.  
  
 Дополнительные сведения о параметрах обработки см. в разделе [обработки объектов &#40;XMLA&#41;](../../xmla/xml-elements-objects.md), и [многомерной модели обработки объекта](../processing-a-multidimensional-model-analysis-services.md).  
  
 В следующем коде выполняется полная обработка всех групп мер указанного куба.  
  
```  
static void FullProcessAllMeasureGroups(Cube cube)  
{  
    foreach (MeasureGroup mg in cube.MeasureGroups)  
        mg.Process(ProcessType.ProcessFull);  
}  
```  
  
##  <a name="Part"></a> Объекты partition  
 Объект <xref:Microsoft.AnalysisServices.Partition> программируется для администрирования и обработки секции.  
  
### <a name="creating-dropping-and-finding-a-partition"></a>Создание, удаление и поиск секции  
 Секции — это простые объекты, которые можно создать за два шага.  
  
1.  Создайте объект секции и заполните его основные атрибуты.  
  
     Основными атрибутами являются «Имя», «Режим хранения», «Источник секции», «Срез», а также другие атрибуты группы мер. Атрибут «Источник секции» определяет инструкцию выборки SQL для текущей секции. Срез — это многомерное выражение, указывающее кортеж или набор, который разграничивает часть измерений, которые содержатся в текущей секции, от родительской группы мер. Для секций MOLAP срезы определяются автоматически при каждой обработке секции.  
  
     Перед созданием секции следует удостовериться, что такая секция не существует. В приведенном ниже образце кода предусмотрено, что если секция существует, то будет удалена и создана повторно.  
  
2.  Обновите сервер при помощи метода Update текущей секции.  
  
     В приведенном далее образце кода все секции обновляются при обновлении куба.  
  
 В приведенном ниже образце кода создаются секции для группы мер «InternetSales».  
  
```  
static void CreateInternetSalesMeasureGroupPartitions(MeasureGroup mg)  
{  
    Partition part;  
    part = mg.Partitions.FindByName("Internet_Sales_184");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_184");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey <= '184'");  
    part.Slice = "[Date].[Calendar Year].&[2001]";  
    part.Annotations.Add("LastOrderDateKey", "184");  
  
    part = mg.Partitions.FindByName("Internet_Sales_549");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_549");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey > '184' AND OrderDateKey <= '549'");  
    part.Slice = "[Date].[Calendar Year].&[2002]";  
    part.Annotations.Add("LastOrderDateKey", "549");  
  
    part = mg.Partitions.FindByName("Internet_Sales_914");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_914");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey > '549' AND OrderDateKey <= '914'");  
    part.Slice = "[Date].[Calendar Year].&[2003]";  
    part.Annotations.Add("LastOrderDateKey", "914");  
}  
```  
  
###  <a name="ProcPart"></a> Обработка секции  
 Процесс обработки секции сводится к использованию метода Process объекта <xref:Microsoft.AnalysisServices.Partition>.  
  
 Дополнительные сведения о параметрах обработки см. в разделе [обработки объектов &#40;XMLA&#41; ](../../xmla/xml-elements-objects.md) и [многомерной модели обработки объекта](../processing-a-multidimensional-model-analysis-services.md).  
  
 В следующем образце кода выполняется полная обработка во всех секциях указанной группы мер.  
  
```  
static void FullProcessAllPartitions(MeasureGroup mg)  
{  
    foreach (Partition part in mg.Partitions)  
        part.Process(ProcessType.ProcessFull);  
}  
```  
  
### <a name="merging-partitions"></a>Слияние секций  
 Слияние секций означает выполнение любых операций, в результате которых две или большее количество секций становятся одной.  
  
 Для слияния секций служит метод объекта <xref:Microsoft.AnalysisServices.Partition>. Эта команда выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции.  
  
 Можно выполнять слияние секций только в том случае, если они удовлетворяют всем перечисленным далее условиям.  
  
-   Секции находятся в одной и той же группе мер.  
  
-   Секции хранятся в одном и том же режиме (MOLAP, HOLAP или ROLAP).  
  
-   Секции находятся на одном сервере; слияние дистанционно расположенных секций можно выполнить, если они находятся на одной сервере.  
  
 В отличие от предыдущих версий в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] нет необходимости, что все исходные секции имели идентичные статистические схемы.  
  
 Итоговым набором агрегатов для целевой секции становится тот же набор агрегатов, который имелся перед выполнением команды слияния.  
  
 В следующем образце кода выполняется слияние всех секций указанной группы мер. Секции сливаются в первую секцию группы мер.  
  
```  
static void MergeAllPartitions(MeasureGroup mg)  
{  
    if (mg.Partitions.Count > 1)  
    {  
        Partition[] partArray = new Partition[mg.Partitions.Count - 1];  
        for (int i = 1; i < mg.Partitions.Count; i++)  
            partArray[i - 1] = mg.Partitions[i];  
        mg.Partitions[0].Merge(partArray);  
        //To have last changes in the server reflected in AMO  
        mg.Refresh();  
    }  
```  
  
##  <a name="AD"></a> Объекты Aggregation  
 Объект <xref:Microsoft.AnalysisServices.Aggregation> программируется в целях разработки проекта агрегата и применения его к одной или нескольким секциям.  
  
### <a name="creating-and-dropping-aggregations"></a>Создание и удаление агрегатов  
 При помощи метода DesignAggregations объекта <xref:Microsoft.AnalysisServices.AggregationDesign> можно легко создавать агрегаты и назначать их группам мер или секциям. Объект <xref:Microsoft.AnalysisServices.AggregationDesign> — это объект, отдельный от секции; объект <xref:Microsoft.AnalysisServices.AggregationDesign> содержится в объекте <xref:Microsoft.AnalysisServices.MeasureGroup>. Агрегаты можно проектировать с учетом достижения указанного уровня оптимизации (числа от 0 до 100) либо до указанного уровня хранения (байты). Одну и ту же статистическую схему можно использовать в нескольких секциях.  
  
 В следующем образце кода создаются агрегаты для всех секций указанной группы мер. Все существующие в секциях агрегаты удаляются.  
  
```  
static public String DesignAggregationsOnPartitions(MeasureGroup mg, double optimizationWanted, double maxStorageBytes)  
{  
    double optimization = 0;  
    double storage = 0;  
    long aggCount = 0;  
    bool finished = false;  
    AggregationDesign ad = null;  
    String aggDesignName;  
    String AggregationsDesigned = "";  
    aggDesignName = mg.AggregationPrefix + "_" + mg.Name;  
    ad = mg.AggregationDesigns.Add();  
    ad.Name = aggDesignName;  
    ad.InitializeDesign();  
    while ((!finished) && (optimization < optimizationWanted) && (storage < maxStorageBytes))  
    {  
        ad.DesignAggregations(out optimization, out storage, out aggCount, out finished);  
    }  
    ad.FinalizeDesign();  
    foreach (Partition part in mg.Partitions)  
    {  
        part.AggregationDesignID = ad.ID;  
        AggregationsDesigned += aggDesignName + " = " + aggCount.ToString() + " aggregations designed\r\n\tOptimization: " + optimization.ToString() + "/" + optimizationWanted.ToString() + "\n\r\tStorage: " + storage.ToString() + "/" + maxStorageBytes.ToString() + " ]\n\r";  
     }  
     return AggregationsDesigned;  
}  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Знакомство с классами объектов AMO](amo-classes-introduction.md)   
 [Классы OLAP объектов AMO](amo-olap-classes.md)   
 [Логическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Обработка объектов многомерной модели](../processing-a-multidimensional-model-analysis-services.md)  
  
  