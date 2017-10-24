---
title: "Программирование объектов интеллектуального анализа данных объектов AMO | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- data mining [AMO]
- AMO, data mining
- Analysis Management Objects, data mining
ms.assetid: d27f58b9-91be-449c-8403-439aa6dd1ff9
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c4c398dbda7bc898d62ea16122ccfba02ea7d5b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-data-mining-objects"></a>Программирование объектов интеллектуального анализа данных AMO
  Программирование объектов интеллектуального анализа данных при помощи объектов AMO осуществляется просто и понятно. Первый шаг заключается в создании модели структуры данных для поддержки проекта интеллектуального анализа. Затем создается модель интеллектуального анализа данных, поддерживающая алгоритм интеллектуального анализа, который будет использоваться для прогнозирования или поиска невидимых связей, лежащих в основе данных. Создав проект интеллектуального анализа данных (в том числе структуру и алгоритмы), можно приступить к обработке моделей интеллектуального анализа данных для получения обученных моделей, которые впоследствии будут использоваться при выполнении запросов и прогнозировании из клиентского приложения.  
  
 Следует, однако, помнить, что объекты AMO не предназначены для запросов; объекты AMO используются для управления и администрирования структур и моделей интеллектуального анализа данных. Чтобы запрашивать данные, используйте [разработка с использованием ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Объекты MiningStructure](#MiningStructure)  
  
-   [Объекты MiningModel](#MiningModel)  
  
##  <a name="MiningStructure"></a>Объекты MiningStructure  
 Структура интеллектуального анализа данных — это определение структуры данных, которое используется для создания всех моделей интеллектуального анализа данных. Структура интеллектуального анализа данных содержит привязку к представлению источника данных, определенному в базе данных, а также определения для всех столбцов, применяемых в моделях интеллектуального анализа данных. Структура может содержать несколько моделей интеллектуального анализа данных.  
  
 Для создания объекта <xref:Microsoft.AnalysisServices.MiningStructure> необходимо выполнить следующие действия.  
  
1.  Создайте объект <xref:Microsoft.AnalysisServices.MiningStructure> и заполните основные атрибуты. Среди основных атрибутов — имя объекта, идентификатор объекта (внутренняя идентификация) и привязка к источнику данных.  
  
2.  Создайте столбцы для модели. Столбцы могут быть скалярными определениями или определениями таблицы.  
  
     У каждого столбца должно быть имя и внутренний идентификатор, тип, определение содержимого и привязка.  
  
3.  Обновите объект <xref:Microsoft.AnalysisServices.MiningStructure> на сервере, используя метод Update объекта.  
  
     Структуры интеллектуального анализа данных можно обрабатывать, а после их обработки может производиться обработка или повторное обучение дочерних моделей интеллектуального анализа.  
  
 В следующем образце кода создается структура интеллектуального анализа данных для прогнозирования объема продаж во временных рядах. Перед выполнением этого образца кода, убедитесь, что базы данных *db*, переданное в качестве параметра для `CreateSalesForecastingMiningStructure`, содержится в `db.DataSourceViews[0]` ссылку на созданное представление *dbo.vTimeSeries* в [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)]образца базы данных.  
  
```  
public static MiningStructure CreateSalesForecastingMiningStructure(Database db)  
{  
    MiningStructure ms = db.MiningStructures.FindByName("Forecasting Sales Structure");  
    if (ms != null)  
        ms.Drop();  
    ms = db.MiningStructures.Add("Forecasting Sales Structure", "Forecasting Sales Structure");  
    ms.Source = new DataSourceViewBinding(db.DataSourceViews[0].ID);  
  
    ScalarMiningStructureColumn amount = ms.Columns.Add("Amount", "Amount");  
    amount.Type = MiningStructureColumnTypes.Double;  
    amount.Content = MiningStructureColumnContents.Continuous;  
    amount.KeyColumns.Add("vTimeSeries", "Amount", OleDbType.Currency);  
  
    ScalarMiningStructureColumn modelRegion = ms.Columns.Add("Model Region", "Model Region");  
    modelRegion.IsKey = true;  
    modelRegion.Type = MiningStructureColumnTypes.Text;  
    modelRegion.Content = MiningStructureColumnContents.Key;  
    modelRegion.KeyColumns.Add("vTimeSeries", "ModelRegion", OleDbType.WChar, 56);  
  
    ScalarMiningStructureColumn qty = ms.Columns.Add("Quantity", "Quantity");  
    qty.Type = MiningStructureColumnTypes.Long;  
    qty.Content = MiningStructureColumnContents.Continuous;  
    qty.KeyColumns.Add("vTimeSeries", "Quantity", OleDbType.Integer);  
  
    ScalarMiningStructureColumn timeIndex = ms.Columns.Add("TimeIndex", "TimeIndex");  
    timeIndex.IsKey = true;  
    timeIndex.Type = MiningStructureColumnTypes.Long;  
    timeIndex.Content = MiningStructureColumnContents.KeyTime;  
    timeIndex.KeyColumns.Add("vTimeSeries", "TimeIndex", OleDbType.Integer);  
  
    ms.Update();  
    return ms;  
}  
```  
  
##  <a name="MiningModel"></a>Объекты MiningModel  
 Модель интеллектуального анализа является репозиторием для всех столбцов и определений столбцов, которые будут использованы в алгоритме интеллектуального анализа.  
  
 Для создания объекта <xref:Microsoft.AnalysisServices.MiningModel> необходимо выполнить следующие действия.  
  
1.  Создайте объект <xref:Microsoft.AnalysisServices.MiningModel> и заполните основные атрибуты.  
  
     Среди основных атрибутов — имя объекта, идентификатор объекта (внутренняя идентификация) и спецификация алгоритма интеллектуального анализа.  
  
2.  Добавьте столбцы модели интеллектуального анализа данных. Один из них должен быть определен как ключ варианта.  
  
3.  Обновите объект <xref:Microsoft.AnalysisServices.MiningModel> на сервере, используя метод Update объекта.  
  
     Объекты <xref:Microsoft.AnalysisServices.MiningModel> могут обрабатываться в родительском объекте <xref:Microsoft.AnalysisServices.MiningStructure> независимо от других моделей.  
  
 В следующем образце кода создается модель прогнозирования временных рядов (Майкрософт), основанная на структуре интеллектуального анализа «Структура прогнозирования продаж».  
  
```  
public static MiningModel CreateSalesForecastingMiningModel(MiningStructure ms)  
{  
    if (ms.MiningModels.ContainsName("Sales Forecasting Model"))  
    {  
        ms.MiningModels["Sales Forecasting Model"].Drop();  
    }  
    MiningModel mm = ms.CreateMiningModel(true, "Sales Forecasting Model");  
    mm.Algorithm = MiningModelAlgorithms.MicrosoftTimeSeries;  
    mm.AlgorithmParameters.Add("PERIODICITY_HINT", "{12}");  
  
    MiningModelColumn amount = new MiningModelColumn();  
    amount.SourceColumnID = "Amount";  
    amount.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn modelRegion = new MiningModelColumn();  
    modelRegion.SourceColumnID = "Model Region";  
    modelRegion.Usage = MiningModelColumnUsages.Key;  
  
    MiningModelColumn qty = new MiningModelColumn();  
    qty.SourceColumnID = "Quantity";  
    qty.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn ti = new MiningModelColumn();  
    ti.SourceColumnID = "TimeIndex";  
    ti.Usage = MiningModelColumnUsages.Key;  
  
    mm.Update();  
    mm.Process(ProcessType.ProcessFull);  
    return mm;  
}  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices>   
 [Основные классы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Классы интеллектуального анализа данных объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)   
 [Логическая архитектура &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

