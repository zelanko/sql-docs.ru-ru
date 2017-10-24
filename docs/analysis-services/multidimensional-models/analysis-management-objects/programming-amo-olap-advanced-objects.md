---
title: "Программирование объектов AMO расширенных объектов OLAP | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: b75f35a7-32df-4f22-983d-324aa98e15a9
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dedfe7e17d6f8fd0be0bb769b9891880a83b2eba
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-olap-advanced-objects"></a>Программирование расширенных объектов AMO OLAP
  В этом разделе рассказывается о программировании объектов AMO объектов OLAP с расширенными возможностями. Этот раздел состоит из следующих подразделов.  
  
-   [Объекты Action](#Action)  
  
-   [Объекты KPI](#KPI)  
  
-   [Объекты перспективы](#Persp)  
  
-   [Объекты ProactiveCaching](#PC)  
  
-   [Объекты Translation](#Transl)  
  
##  <a name="Action"></a>Объекты Action  
 Классы действий позволяют создавать активные ответные действия во время просмотра определенных областей куба. Объекты действий можно определять при помощи объектов AMO, но они используются из клиентского приложения, просматривающего данные. Действия могут быть разных типов, поэтому их создание должно осуществляться в соответствии с их типом. Действия могут представлять собой следующее.  
  
-   Действия детализации, которые возвращают набор строк, представляющих основополагающие данные выделенных ячеек куба, в которых происходит действие.  
  
-   Действия формирования отчета, которые возвращают из служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] отчет, относящийся к выделенной секции куба, в которой происходит действие.  
  
-   Стандартные действия, которые возвращают элемент действия (URL, HTML, DataSet, RowSet и другие элементы), связанный с выделенной секцией куба, в которой происходит действие.  
  
 Для создания объекта действия требуется выполнить следующие шаги.  
  
1.  Создайте производный объект действия и заполните основные атрибуты.  
  
     Основными являются следующие атрибуты: тип действия, тип целевого объекта или раздел куба, целевая или определенная область куба, в которой доступно действие, заголовок, а также область, в которой заголовок является многомерным выражением.  
  
2.  Заполните конкретные атрибуты типа действия.  
  
     У трех типов действий — разные атрибуты; параметры см. в приведенном ниже образце кода.  
  
3.  Добавьте действие в коллекцию кубов и обновите куб. Действие не является обновляемым объектом.  
  
 Для проверки действия требуется другая прикладная программа. Проверить действие можно в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Во-первых, необходимо установить [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] примеры см. в разделе [обработка многомерной модели &#40; Службы Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 В следующем образце кода выполняется репликация трех разных действий из образца Adventure Works Analysis Services Project. Действия можно различать, поскольку имена действий, введенных при помощи следующего образца, начинаются с «My».  
  
```  
static public void CreateActions(Cube cube)  
{  
    #region Adding a drillthrough action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My Reseller Details"))  
        cube.Actions.Remove("My Drillthrough Action",true);  
  
    //Create a Drillthrough action  
    DrillThroughAction dtaction = new DrillThroughAction("My Reseller Details", "My Drillthrough Action");  
  
    //Define the Action  
    dtaction.Type = ActionType.DrillThrough;  
    dtaction.TargetType = ActionTargetType.Cells;  
    dtaction.Target = "MeasureGroupMeasures(\"Reseller Sales\")";  
    dtaction.Caption = "My Drillthrough...";  
    dtaction.CaptionIsMdx = false;  
  
    #region create drillthrough action specifics  
    //Adding Drillthrough columns  
    //Adding Measure columns to the drillthrough  
    MeasureGroup mg = cube.MeasureGroups.FindByName("Reseller Sales");  
    MeasureBinding mb1 = new MeasureBinding();  
    mb1.MeasureID = mg.Measures.FindByName( "Reseller Sales Amount").ID;  
    dtaction.Columns.Add(mb1);  
  
    MeasureBinding mb2 = new MeasureBinding();  
    mb2.MeasureID = mg.Measures.FindByName("Reseller Order Quantity").ID;  
    dtaction.Columns.Add(mb2);  
  
    MeasureBinding mb3 = new MeasureBinding();  
    mb3.MeasureID = mg.Measures.FindByName("Reseller Unit Price").ID;  
    dtaction.Columns.Add(mb3);  
  
    //Adding Dimension Columns to the drillthrough  
    CubeAttributeBinding cb1 = new CubeAttributeBinding();  
    cb1.CubeID = cube.ID;  
    cb1.CubeDimensionID = cube.Dimensions.FindByName("Reseller").ID;  
    cb1.AttributeID = "Reseller Name";  
    cb1.Type = AttributeBindingType.All;  
    dtaction.Columns.Add(cb1);  
  
    CubeAttributeBinding cb2 = new CubeAttributeBinding();  
    cb2.CubeID = cube.ID;  
    cb2.CubeDimensionID = cube.Dimensions.FindByName("Product").ID;  
    cb2.AttributeID = "Product Name";  
    cb2.Type = AttributeBindingType.All;  
    dtaction.Columns.Add(cb2);  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(dtaction);  
    #endregion  
  
    #region Adding a Standard action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My City Map"))  
        cube.Actions.Remove("My Action", true);  
  
    //Create a Drillthrough action  
    StandardAction stdaction = new StandardAction("My City Map", "My Action");  
  
    //Define the Action  
    stdaction.Type = ActionType.Url;  
    stdaction.TargetType = ActionTargetType.AttributeMembers;  
    stdaction.Target = "[Geography].[City]";  
    stdaction.Caption = "\"My View Map for \" + [Geography].[City].CurrentMember.Member_Caption + \"...\"";  
    stdaction.CaptionIsMdx = true;  
  
    #region create standard action specifics  
    stdaction.Expression = "\"http://maps.msn.com/home.aspx?plce1=\" + " +  
        "[Geography].[City].CurrentMember.Name + \",\" + " +  
        "[Geography].[State-Province].CurrentMember.Name + \",\" + " +  
        "[Geography].[Country].CurrentMember.Name + " +  
        "\"&regn1=\" + " +  
        "Case " +  
            "When [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[Australia] " +  
                "Then \"3\" " +  
            "When [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[Canada] " +  
                "Or [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[United States] " +  
                "Then \"0\" " +  
                "Else \"1\" " +  
        "End ";  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(stdaction);  
  
    #endregion  
  
    #region Adding a Reporting action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My Sales Reason Comparisons"))  
        cube.Actions.Remove("My Report Action", true);  
  
    //Create a Report action  
    ReportAction rsaction = new ReportAction("My Sales Reason Comparisonsp", "My Report Action");  
  
    //Define the Action  
    rsaction.Type = ActionType.Report;  
    rsaction.TargetType = ActionTargetType.AttributeMembers;  
    rsaction.Target = "[Product].[Category]";  
    rsaction.Caption = "\"My Sales Reason Comparisons for \" + [Product].[Category].CurrentMember.Member_Caption + \"...\"";  
    rsaction.CaptionIsMdx = true;  
  
    #region create Report action specifics  
    rsaction.ReportServer = "MyRSSamplesServer";  
    rsaction.Path = "ReportServer?/AdventureWorks Sample Reports/Sales Reason Comparisons";  
    rsaction.ReportParameters.Add("ProductCategory", "UrlEscapeFragment( [Product].[Category].CurrentMember.UniqueName )");  
    rsaction.ReportFormatParameters.Add("rs:Command", "Render");  
    rsaction.ReportFormatParameters.Add("rs:Renderer", "HTML5");  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(rsaction);  
  
    #endregion  
}  
```  
  
##  <a name="KPI"></a>Объекты KPI  
 Ключевой показатель эффективности представляет собой коллекцию вычислений, связанных с группой мер куба и используемых для оценки успешности бизнеса. Объекты <xref:Microsoft.AnalysisServices.Kpi> можно определять при помощи объектов AMO, но для их использования служит клиентское приложение, предназначенное для просмотра данных.  
  
 Для создания объекта <xref:Microsoft.AnalysisServices.Kpi> необходимо выполнить следующие действия.  
  
1.  Создайте объект <xref:Microsoft.AnalysisServices.Kpi> и заполните основные атрибуты.  
  
     Список основных атрибутов: «Описание», «Папка отображения», «Связанная группа мер» и «Значение». Атрибут «Папка отображения» указывает клиентскому приложению, где следует размещать ключевые показатели эффективности для конечного пользователя. Атрибут «Связанная группа мер» указывает группу мер, с которой следует связывать все вычисления многомерных выражений. Атрибут «Значение» показывает фактическое значение показателя эффективности в виде многомерного выражения.  
  
2.  Определите ключевые показатели эффективности: «Цель», «Состояние» и «Тренд».  
  
     Индикаторы являются многомерными выражениями, которые должны иметь значение в диапазоне от -1 до 1, но диапазон значений для индикаторов определяет приложение, в котором осуществляется просмотр.  
  
3.  При просмотре ключевых показателей эффективности в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] значения менее -1 принимаются за -1, а значения более 1 принимаются за 1.  
  
4.  Определите графические изображения.  
  
     Графические изображения представляют собой строковые значения, используемые в клиентском приложении в качестве ссылок для указания правильного набора выводимых изображений. Строка графического изображения определяет также поведение функции отображения. Обычно диапазон разбивается на нечетное число состояний, от плохого к хорошему, каждому из которых присваивается изображение из набора.  
  
     Если для обзора ключевых показателей эффективности используется среда [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], то диапазон индикатора разбивается в зависимости от имен на три или пять состояний. Кроме того, есть имена, при которых диапазон инвертируется, то есть -1 рассматривается как состояние «Хорошо», а 1 — «Плохо». В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] в этом диапазоне имеется три следующих состояния:  
  
    -   Плохо = от -1 до -0,5.  
  
    -   Приемлемо = от -0,4999 до 0,4999.  
  
    -   Хорошо = от 0,50 до 1.  
  
     В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] в этом диапазоне имеется пять следующих состояний:  
  
    -   Плохо = от -1 до -0,75.  
  
    -   Рискованно = от -0,7499 до -0,25.  
  
    -   Приемлемо = от -0,2499 до 0,2499.  
  
    -   Повышение = от 0,25 до 0,7499.  
  
    -   Хорошо = от 0,75 до 1.  
  
 В следующей таблице показано назначение, имя и число состояний, связанное с изображением.  
  
|Назначение изображения|Имя изображения|Число состояний|  
|-----------------|----------------|----------------------|  
|Состояние|Фигуры|3|  
|Состояние|Светофор|3|  
|Состояние|Дорожные знаки|3|  
|Состояние|Датчик|3|  
|Состояние|Обратная шкала|5|  
|Состояние|Термометр|3|  
|Состояние|Цилиндр|3|  
|Состояние|Лица|3|  
|Состояние|Стрелка отклонения|3|  
|Тренд|Стандартная стрелка|3|  
|Тренд|Стрелка состояния|3|  
|Тренд|Обратная стрелка состояния|5|  
|Тренд|Лица|3|  
  
1.  Добавьте ключевой показатель эффективности в коллекцию кубов и обновите куб, так как ключевой показатель эффективности не является обновляемым объектом.  
  
 Для проверки ключевого показателя эффективности требуется другая прикладная программа. Проверить ключевой показатель эффективности можно в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 В следующем образце кода создается ключевой показатель эффективности в папке «Финансовая перспектива/Рост прибыли» для куба Adventure Works, который включен в образец «Adventure Works Analysis Services Project».  
  
```  
static public void CreateKPIs(Cube cube)  
{  
    Kpi kpi = cube.Kpis.Add("My Internet Revenue", "My Internet Revenue");  
    kpi.Description = "(My) Revenue achieved through direct sales via Interner";  
    kpi.DisplayFolder = "\\Financial Perspective\\Grow Revenue";  
    kpi.AssociatedMeasureGroupID = "Internet Sales";  
    kpi.Value = "[Measures].[Internet Sales Amount]";  
    #region Goal  
    kpi.Goal = "Case" +  
               "     When IsEmpty" +  
               "          (" +  
               "            ParallelPeriod" +  
               "            (" +  
               "              [Date].[Fiscal Time].[Fiscal Year]," +  
               "              1," +  
               "              [Date].[Fiscal Time].CurrentMember" +  
               "            )" +  
               "          )" +   
               "     Then [Measures].[Internet Sales Amount]" +  
               "     Else 1.10 *" +  
               "          (" +  
               "            [Measures].[Internet Sales Amount]," +  
               "            ParallelPeriod" +  
               "            (" +  
               "              [Date].[Fiscal Time].[Fiscal Year]," +  
               "              1," +  
               "              [Date].[Fiscal Time].CurrentMember" +  
               "            )" +  
               "          ) " +  
               " End";  
    #endregion  
    #region Status  
    kpi.Status = "Case" +  
                 "   When KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) >= .95 " +  
                 "   Then 1 " +  
                 "   When KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) <  .95 " +  
                 "        And  " +  
                 "        KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) >= .85 " +  
                 "   Then 0 " +  
                 "   Else -1 " +  
                 "End";  
    #endregion  
    #region Trend  
    kpi.Trend = "Case " +  
                "    When VBA!Abs " +  
                "         ( " +  
                "           KpiValue( \"Internet Revenue\" ) -  " +  
                "           ( " +  
                "             KpiValue ( \"Internet Revenue\" ), " +  
                "             ParallelPeriod " +  
                "             (  " +  
                "               [Date].[Fiscal Time].[Fiscal Year], " +  
                "               1, " +  
                "               [Date].[Fiscal Time].CurrentMember " +  
                "             ) " +  
                "           ) / " +  
                "           ( " +  
                "             KpiValue ( \"Internet Revenue\" ), " +  
                "             ParallelPeriod " +  
                "             (  " +  
                "               [Date].[Fiscal Time].[Fiscal Year], " +  
                "               1, " +  
                "               [Date].[Fiscal Time].CurrentMember " +  
                "             ) " +  
                "           )   " +  
                "         ) <=.02  " +  
                "    Then 0 " +  
                "    When KpiValue( \"Internet Revenue\" ) -  " +  
                "         ( " +  
                "           KpiValue ( \"Internet Revenue\" ), " +  
                "           ParallelPeriod " +  
                "           (  " +  
                "             [Date].[Fiscal Time].[Fiscal Year], " +  
                "             1, " +  
                "             [Date].[Fiscal Time].CurrentMember " +  
                "           ) " +  
                "         ) / " +  
                "         ( " +  
                "           KpiValue ( \"Internet Revenue\" ), " +  
                "           ParallelPeriod " +  
                "           (  " +  
                "             [Date].[Fiscal Time].[Fiscal Year], " +  
                "             1, " +  
                "             [Date].[Fiscal Time].CurrentMember " +  
                "           ) " +  
                "         )  >.02 " +  
                "    Then 1 " +  
                "    Else -1 " +  
                "End";  
    #endregion  
    kpi.TrendGraphic = "Standard Arrow";  
    kpi.StatusGraphic = "Cylinder";  
}.  
```  
  
##  <a name="Persp"></a>Объекты перспективы  
 Объекты <xref:Microsoft.AnalysisServices.Perspective> можно определять при помощи объектов AMO, но для их использования служит клиентское приложение, предназначенное для просмотра данных.  
  
 Для создания объекта <xref:Microsoft.AnalysisServices.Perspective> необходимо выполнить следующие действия.  
  
1.  Создайте объект <xref:Microsoft.AnalysisServices.Perspective> и заполните основные атрибуты.  
  
     Список основных атрибутов: «Имя», «Мера по умолчанию», «Описание» и заметки.  
  
2.  Добавьте все объекты из родительского куба, которые должен видеть конечный пользователь.  
  
     Добавьте измерения куба (атрибуты и иерархии), группы мер (меру и группу мер), действия, ключевые показатели эффективности и вычисления.  
  
3.  Добавьте перспективу в коллекцию кубов и обновите куб, так как перспектива не является обновляемым объектом.  
  
 Для проверки перспективы требуется другая прикладная программа. Проверить перспективу можно в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 В следующем образце кода для указанного куба создается перспектива «Прямые продажи».  
  
```  
static public void CreatePerspectives(Cube cube)  
{  
    Perspective perspective = cube.Perspectives.Add("Direct Sales", "Direct Sales");  
    CubeDimension dim1 = cube.Dimensions.GetByName("Date");  
    PerspectiveDimension pdim1 = perspective.Dimensions.Add(dim1.DimensionID);  
    pdim1.Attributes.Add("Date");  
    pdim1.Attributes.Add("Calendar Year");  
    pdim1.Attributes.Add("Fiscal Year");  
    pdim1.Attributes.Add("Calendar Quarter");  
    pdim1.Attributes.Add("Fiscal Quarter");  
    pdim1.Attributes.Add("Calendar Month Number");  
    pdim1.Attributes.Add("Fiscal Month Number");  
    pdim1.Hierarchies.Add("Calendar Time");  
    pdim1.Hierarchies.Add("Fiscal Time");  
  
    CubeDimension dim2 = cube.Dimensions.GetByName("Product");  
    PerspectiveDimension pdim2 = perspective.Dimensions.Add(dim2.DimensionID);  
    pdim2.Attributes.Add("Product Name");  
    pdim2.Attributes.Add("Product Line");  
    pdim2.Attributes.Add("Model Name");  
    pdim2.Attributes.Add("List Price");  
    pdim2.Attributes.Add("Size");  
    pdim2.Attributes.Add("Weight");  
    pdim2.Hierarchies.Add("Product Model Categories");  
    pdim2.Hierarchies.Add("Product Categories");  
  
    PerspectiveMeasureGroup pmg = perspective.MeasureGroups.Add("Internet Sales");  
    pmg.Measures.Add("Internet Sales Amount");  
    pmg.Measures.Add("Internet Order Quantity");  
    pmg.Measures.Add("Internet Unit Price");  
  
    pmg = perspective.MeasureGroups.Add("Reseller Sales");  
    pmg.Measures.Add("Reseler Sales Amount");  
    pmg.Measures.Add("Reseller Order Quantity");  
    pmg.Measures.Add("Reseller Unit Price");  
  
    PerspectiveAction pact = perspective.Actions.Add("Drillthrough Action");  
  
    PerspectiveKpi pkpi = perspective.Kpis.Add("Internet Revenue");  
    Cube.Update();  
}  
```  
  
##  <a name="PC"></a>Объекты ProactiveCaching  
 Объекты <xref:Microsoft.AnalysisServices.ProactiveCaching> можно определять при помощи объектов AMO.  
  
 Для создания объекта <xref:Microsoft.AnalysisServices.ProactiveCaching> необходимо выполнить следующие действия.  
  
1.  Создайте объект <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
     Для него не нужно определять основные атрибуты.  
  
2.  Добавьте спецификации кэша.  
  
|Спецификация|Описание|  
|-------------------|-----------------|  
|AggregationStorage|Тип хранилища для агрегатов.<br /><br /> Относится только к секции. В измерении значение должно быть **Regular.**|  
|SilenceInterval|Минимальное количество времени существования кэша до начала создания образа MOLAP.|  
|Задержка|Количество времени, которое проходит от момента самого раннего уведомления до момента удаления образов MOLAP.|  
|SilenceOverrideInterval|Время после первоначального уведомления, по истечении которого создание образа MOLAP будет запущено безусловно.|  
|ForceRebuildInterval|Время (начиная с момента удаления образа MOLAP), по истечении которого создание образа MOLAP начнется безусловно (без уведомлений).|  
|OnlineMode|Когда имеется образ MOLAP.<br /><br /> Может представлять собой либо **Immediate** , либо **OnCacheComplete**.|  
  
1.  Добавьте объект <xref:Microsoft.AnalysisServices.ProactiveCaching> в родительскую коллекцию. Потребуется обновить родительскую коллекцию, так как объект <xref:Microsoft.AnalysisServices.ProactiveCaching> не является обновляемым.  
  
 В следующем образце кода создается объект <xref:Microsoft.AnalysisServices.ProactiveCaching> во всех секциях из группы мер «Продажи через Интернет» в кубе Adventure Works из указанной базы данных.  
  
```  
static public void SetProactiveCachingSettings(Database db)  
{  
    ProactiveCaching pc;  
    if (db.Cubes.ContainsName("Adventure Works") && db.Cubes.FindByName("Adventure Works").MeasureGroups.ContainsName("Internet Sales"))  
    {  
        ProactiveCachingTablesBinding pctb;  
        TableNotification tn;  
  
        MeasureGroup mg = db.Cubes.FindByName("Adventure Works").MeasureGroups.FindByName("Internet Sales");  
        foreach(Partition part in mg.Partitions)  
        {  
            pc = new ProactiveCaching();  
            pc.AggregationStorage = ProactiveCachingAggregationStorage.MolapOnly;  
            pc.SilenceInterval = TimeSpan.FromSeconds(10);  
            pc.Latency = TimeSpan.FromSeconds(-1);  
            pc.SilenceOverrideInterval = TimeSpan.FromMinutes(10);  
            pc.ForceRebuildInterval = TimeSpan.FromSeconds(-1);  
            pc.Enabled = true;  
            pc.OnlineMode = ProactiveCachingOnlineMode.OnCacheComplete;  
            pctb = new ProactiveCachingTablesBinding();  
            pctb.NotificationTechnique = NotificationTechnique.Server;  
            tn = new TableNotification("[FactInternetSales]", "dbo");  
            pctb.TableNotifications.Add( tn);  
            pc.Source = pctb;  
  
            part.ProactiveCaching = pc;  
            part.Update();  
        }  
    }  
}  
```  
  
##  <a name="Transl"></a>Объекты Translation  
 Объекты переводов можно определять при помощи объектов AMO, но для их использования служит клиентское приложение, применяемое для просмотра данных. Объекты переводов просты в программировании. Переводы заголовков объектов обеспечиваются парами «Локаль языка» и «Переведенный заголовок». Для любого заголовка можно разрешить несколько переводов. Переводы можно предусмотреть для большинства объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], например измерений, атрибутов, иерархий, кубов, групп мер, мер и др.  
  
 Следующий образец кода обеспечивает перевод на испанский язык имени атрибута «Название продукта».  
  
```  
static public void CreateTranslations(Database db)  
{  
    //Spanish Tranlations for Product Category in Product Dimension  
    Dimension dim = db.Dimensions["Product"];  
    DimensionAttribute atr = dim.Attributes["Product Name"];  
    Translation tran = atr.Translations.Add(3082);  
    tran.Caption = "Nombre Producto";  
  
    dim.Update(UpdateOptions.ExpandFull);  
  
}  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices>   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Классы OLAP объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)   
 [Логическая архитектура &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Обработка многомерной модели &#40; Службы Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Установка образцов данных и проектов для служб Analysis Services многомерное моделирование учебник](../../../analysis-services/install-sample-data-and-projects.md)  
  
  

