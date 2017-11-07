---
title: "Работа с объектной моделью ADOMD.NET | Документы Microsoft"
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
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 81a9272284e662eb7f5f47e464e85e324b92a39d
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="retrieving-metadata---working-with-adomdnet-object-model"></a>Извлечение метаданных - работа с объектной моделью ADOMD.NET
  Компонент ADOMD.NET предоставляет модель объектов для просмотра кубов и подчиненных объектов, содержащихся в источниках аналитических данных. Однако эта модель объектов предоставляет доступ не ко всем метаданным для источника аналитических данных. Модель объектов обеспечивает доступ только к наиболее полезным сведениям, которые будет отображать клиентское приложение, чтобы пользователь мог составлять команды в интерактивном режиме. Представляемые метаданные имеют менее высокую сложность, поэтому модель объектов ADOMD.NET проще использовать.  
  
 В модели объектов ADOMD.NET объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> предоставляет доступ к сведениям в кубах оперативной аналитической обработки (OLAP) и моделях интеллектуального анализа данных, определенных для источника аналитических данных, а также таких связанных объектах, как измерения, именованные наборы и алгоритмы интеллектуального анализа.  
  
## <a name="retrieving-olap-metadata"></a>Извлечение метаданных OLAP  
 Каждый объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> имеет коллекцию объектов <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>, которые представляют кубы, доступные для пользователя, или приложения. Объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> выдает информацию о кубах, а также о различных объектах, связанных с кубами, таких как измерения, ключевые показатели эффективности, меры, именованные наборы и т. д.  
  
 При возможности используйте объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> для представления метаданных в клиентских приложениях, предназначенных для поддержки нескольких серверов OLAP или для достижения общих целей отображения метаданных и доступа.  
  
> [!NOTE]  
>  Для извлечения метаданных, характерных для поставщика, или для отображения и доступа к подробным метаданным используйте наборы строк схемы. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующем примере объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> используется для извлечения видимых кубов и их измерений из локального сервера:  
  
 [!code-cs[Adomd.NetClient#RetrieveCubesAndDimensions](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-metadata-work_1_1.cs)]  
  
## <a name="retrieving-data-mining-metadata"></a>Извлечение метаданных интеллектуального анализа данных  
 Каждый объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> имеет несколько коллекций, предоставляющих сведения о возможностях источника данных по интеллектуальному анализу данных.  
  
-   Коллекция <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> содержит список всех моделей интеллектуального анализа данных в источнике данных.  
  
-   Коллекция <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> содержит сведения о доступных алгоритмах интеллектуального анализа данных.  
  
-   Коллекция <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> предоставляет доступ к сведениям о структурах интеллектуального анализа данных на сервере.  
  
 Чтобы определить, как выполнять запросы к модели интеллектуального анализа на сервере, последовательно просмотрите коллекцию <xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A>. Каждый объект <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn> выдает следующие характеристики.  
  
-   Является ли объект входным столбцом (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>).  
  
-   Является ли объект прогнозируемым столбцом (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>).  
  
-   Значения, связанные с дискретным столбцом (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>).  
  
-   Тип данных в столбце (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>).  
  
## <a name="see-also"></a>См. также:  
 [Получение метаданных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  

