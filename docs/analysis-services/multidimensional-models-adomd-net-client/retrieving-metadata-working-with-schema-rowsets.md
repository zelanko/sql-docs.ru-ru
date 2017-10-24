---
title: "Работа с наборами строк схемы в ADOMD.NET | Документы Microsoft"
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
- retrieving metadata
- schema rowsets [ADOMD.NET]
ms.assetid: 7bf75bf8-f1e1-44f6-ac42-c38a681654cf
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 37a9b92672496c6eebc50a99b2ea0cacee55372a
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="retrieving-metadata---working-with-schema-rowsets"></a>Извлечение метаданных - работа с наборы строк схемы
  Если требуется больший объем метаданных, чем тот, который доступен в объектной модели ADOMD.NET, компонент ADOMD.NET имеет возможность извлекать полный спектр наборов строк схемы XML для аналитики (XMLA), OLE DB, OLE DB для OLAP и OLE DB для интеллектуального анализа данных.  
  
 **Метаданные XML для аналитики**  
 Наборы строк схемы XML для аналитики предоставляют метод для получения сведений низкого уровня о сервере. Эти сведения включают имеющиеся на сервере источники данных, ключевые слова, зарезервированные поставщиком, литералы, поддерживаемые поставщиком и др. Набор строк схемы XML для аналитики можно использовать даже для обнаружения всех наборов строк схемы, поддерживаемых поставщиком.  
  
 Дополнительные сведения: [XML для аналитики наборы строк схемы](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 **Метаданные OLE DB**  
 Наборы строк схемы OLE DB предоставляют метод получения сведений от различных поставщиков, стандартный для отрасли.  
  
 Дополнительные сведения: [строк схемы OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
 **Метаданные OLAP**  
 Сведения схемы, предоставленные для источника аналитических данных, включают базы данных или каталоги, доступные из этого источника аналитических данных, кубы и модели интеллектуального анализа в базе данных, роли, существующие для кубов в источнике данных и др.  
  
 Дополнительные сведения: [OLE DB для OLAP наборов строк схемы](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
 **Метаданные интеллектуального анализа данных**  
 Помимо метаданных OLAP, при помощи наборов строк схемы можно получать и метаданные интеллектуального анализа данных. Доступные наборы строк выдают сведения об имеющихся в базе данных моделях интеллектуального анализа данных, имеющихся алгоритмах интеллектуального анализа, требуемых алгоритмом параметрах, структурах интеллектуального анализа и др.  
  
 Дополнительные сведения: [наборы строк схемы интеллектуального анализа](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
 Метаданные из каждого из этих различных наборов строк схемы извлекаются путем передачи идентификатора GUID или имени XMLA с методом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
## <a name="retrieving-metadata-by-passing-guids"></a>Получение метаданных с помощью передачи идентификаторов GUID  
 Класс <xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid> содержит список полей, представляющих наборы строк схемы, которые обычно поддерживаются поставщиками и источниками аналитических данных. Чтобы получить от источника аналитических данных или поставщика как общие метаданные, так и метаданные, характерные для этого поставщика, с одним из следующих методов используются идентификаторы GUID, содержащиеся в объекте <xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid>:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
> [!NOTE]  
>  Поставщик данных ADOMD.NET обеспечивает доступ к сведениям схемы с помощью функциональных средств, предоставляемых конкретным поставщиком и источником аналитических данных. Каждый поставщик и источник данных могут предоставлять разные метаданные.  
  
## <a name="retrieving-metadata-by-passing-xmla-names"></a>Получение метаданных при помощи передачи имен XMLA  
 Следующие методы в качестве аргументов принимают имя схемы XMLA, указывающее, сведения какой схемы должны быть возвращены, а также массив ограничений на возвращаемые столбцы:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
 Каждый из этих методов возвращает экземпляр **набора данных** , заполненный данными схемы. **DataSet** объект относится **System.Data** пространство имен библиотеки классов Microsoft .NET Framework.  
  
## <a name="example"></a>Пример  
 В следующем примере функция GetActions принимает соединение, имя куба, координату и тип координаты, извлекает [строк MDSCHEMA_ACTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)и возвращает действия, доступные в выбранной координате.  
  
 [!code-cs[Adomd.NetClient#GetActions](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-metadata-work_0_1.cs)]  
  
## <a name="see-also"></a>См. также:  
 [Получение метаданных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  

