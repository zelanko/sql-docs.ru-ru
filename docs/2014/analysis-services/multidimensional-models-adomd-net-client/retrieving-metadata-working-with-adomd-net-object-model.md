---
title: Работа с объектной моделью ADOMD.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ceb363b3911afb3a1ea21d51e6a65eff09cd3f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328544"
---
# <a name="working-with-the-adomdnet-object-model"></a>Работа с объектной моделью ADOMD.NET
  Компонент ADOMD.NET предоставляет модель объектов для просмотра кубов и подчиненных объектов, содержащихся в источниках аналитических данных. Однако эта модель объектов предоставляет доступ не ко всем метаданным для источника аналитических данных. Модель объектов обеспечивает доступ только к наиболее полезным сведениям, которые будет отображать клиентское приложение, чтобы пользователь мог составлять команды в интерактивном режиме. Представляемые метаданные имеют менее высокую сложность, поэтому модель объектов ADOMD.NET проще использовать.  
  
 В модели объектов ADOMD.NET объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> предоставляет доступ к сведениям в кубах оперативной аналитической обработки (OLAP) и моделях интеллектуального анализа данных, определенных для источника аналитических данных, а также таких связанных объектах, как измерения, именованные наборы и алгоритмы интеллектуального анализа.  
  
## <a name="retrieving-olap-metadata"></a>Извлечение метаданных OLAP  
 Каждый объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> имеет коллекцию объектов <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>, которые представляют кубы, доступные для пользователя, или приложения. Объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> выдает информацию о кубах, а также о различных объектах, связанных с кубами, таких как измерения, ключевые показатели эффективности, меры, именованные наборы и т. д.  
  
 При возможности используйте объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> для представления метаданных в клиентских приложениях, предназначенных для поддержки нескольких серверов OLAP или для достижения общих целей отображения метаданных и доступа.  
  
> [!NOTE]  
>  Для извлечения метаданных, характерных для поставщика, или для отображения и доступа к подробным метаданным используйте наборы строк схемы. Дополнительные сведения см. в разделе [Working with Schema Rowsets in ADOMD.NET](retrieving-metadata-working-with-schema-rowsets.md)).  
  
 В следующем примере объект <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> используется для извлечения видимых кубов и их измерений из локального сервера:  
  
 [!code-csharp[Adomd.NetClient#RetrieveCubesAndDimensions](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#retrievecubesanddimensions)]  
  
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
  
## <a name="see-also"></a>См. также  
 [Получение метаданных из источника аналитических данных](retrieving-metadata-from-an-analytical-data-source.md)  
  
  
