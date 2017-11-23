---
title: "Получение метаданных из источника аналитических данных | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- metadata [ADOMD.NET]
- retrieving metadata
ms.assetid: 00043ebd-7164-4ceb-b945-6e44378ea00a
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c7c280b4b4a996d68bb403ea6210322604452e5d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="retrieving-metadata-from-an-analytical-data-source"></a>Получение метаданных из источника аналитических данных
  Метаданные важны для приложений, которые получают и работают с аналитическими данными. При получении данных из реляционного источника данных их размерность является прогнозируемой даже при наличии вложенных наборов данных. По своей структуре результирующие наборы из реляционной базы данных обычно являются двухмерными или скалярными. Однако данные, получаемые из источников аналитических данных, могут иметь переменную размерность и быть организованными в потенциально глубокие иерархии.  
  
 Для решения сложных задач извлечения метаданных из источников аналитических данных компонент ADOMD.NET предоставляет две формы получения метаданных.  
  
 **Модель объектов**  
 Использовать модель объектов компонента ADOMD.NET в целом проще, чем наборы строк схемы. В большинстве случаев для доступа к метаданным различных объектов базы данных достаточно воспользоваться моделью объектов. Доступ к объектной модели компонента ADOMD.NET можно получить через <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Дополнительные сведения: [работа с объектной моделью ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-adomd-net-object-model.md)  
  
 **Наборы строк схемы**  
 Полным, но и более сложным вариантом извлечения метаданных является использование наборов строк схемы. Набор строк схемы является набором строк OLE DB, который инкапсулирует в себя описание всех объектов определенного типа в базе данных. Сведения схемы в источнике аналитических данных включают базы данных или каталоги, доступные из этого источника данных, кубы и модели интеллектуального анализа в базе данных, роли, существующие для кубов в источнике данных, и т. д. Эти метаданные могут быть получены с помощью <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> метод, передав ему либо **GUID** или XML для аналитики (XMLA) имя.  
  
 Дополнительные сведения: [работа с наборами строк схемы в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)  
  
 Каждый из этих способов получения метаданных открывает доступ к метаданным различных типов. В следующей таблице описываются различные метаданные, которые можно получить с помощью каждого метода, а также методы, используемые для их получения.  
  
|Идентификатор GUID (используется в наборах строк схемы)|Имя XMLA (используется в наборах строк схемы)|Модель объектов ADOMD.NET|  
|-------------------------------------|------------------------------------------|----------------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Actions>|[Набор строк MDSCHEMA_ACTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Catalogs>|[Набор строк DBSCHEMA_CATALOGS](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Columns>|[Набор строк DBSCHEMA_COLUMNS](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Connections>|**DISCOVER_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Cubes>|[Набор строк MDSCHEMA_CUBES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|AdomdConnection.Cubes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DataSources>|[Набор строк DISCOVER_DATASOURCES](../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DBConnections>|**DISCOVER_DB_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Dimensions>|[Набор строк MDSCHEMA_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|AdomdConnection.Cubes[].Dimensions|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DimensionStat>|**DISCOVER_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Enumerators>|[Набор строк DISCOVER_ENUMERATORS](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Functions>|[Набор строк MDSCHEMA_FUNCTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Hierarchies>|[Набор строк MDSCHEMA_HIERARCHIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.InputDataSources>|[Набор строк MDSCHEMA_INPUT_DATASOURCES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Instances>|[Набор строк DISCOVER_INSTANCES](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Jobs>|**DISCOVER_JOBS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Keywords>|[Набор строк DISCOVER_KEYWORDS &#40; OLE DB для OLAP &#41;](../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Kpis>|[Набор строк MDSCHEMA_KPIS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|AdomdConnection.Cubes[].KPIs|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Levels>|[Набор строк MDSCHEMA_LEVELS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Literals>|[Набор строк DISCOVER_LITERALS](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locations>|**DISCOVER_LOCATIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locks>|**DISCOVER_LOCKS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MasterKey>|**DISCOVER_MASTER_KEY**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroupDimensions>|[Набор строк MDSCHEMA_MEASUREGROUP_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroups>|[Набор строк MDSCHEMA_MEASUREGROUPS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Measures>|[Набор строк MDSCHEMA_MEASURES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|AdomdConnection.Cubes[].Measures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemberProperties>|[Набор строк MDSCHEMA_PROPERTIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|Коллекция PropertyCollection, доступная из большинства основных объектов ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Members>|[Набор строк MDSCHEMA_MEMBERS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels[].GetMembers()|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryGrant>|**DISCOVER_MEMORYGRANT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryUsage>|**DISCOVER_MEMORYUSAGE**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningColumns>|[Набор строк DMSCHEMA_MINING_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|AdomdConnection.MiningModels[].MiningModelColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningFunctions>|[Набор строк DMSCHEMA_MINING_FUNCTIONS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContent>|[Набор строк DMSCHEMA_MINING_MODEL_CONTENT](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|AdomdConnection.MiningModels[].MiningContentNodes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContentPmml>|[Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModels>|[Набор строк DMSCHEMA_MINING_MODELS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|AdomdConnection.MiningModels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelXml>|[Набор строк DMSCHEMA_MINING_MODEL_XML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServiceParameters>|[Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|AdomdConnection.MiningServices[].MiningServiceParameters|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServices>|[Набор строк DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|AdomdConnection.MiningServices|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructureColumns>|[Набор строк DMSCHEMA_MINING_STRUCTURE_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|AdomdConnection.MiningStructures[].MiningStructureColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructures>|[Набор строк DMSCHEMA_MINING_STRUCTURES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|AdomdConnection.MiningStructures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionDimensionStat>|**DISCOVER_PARTITION_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionStat>|**DISCOVER_PARTITION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PerformanceCounters>|**DISCOVER_PERFORMANCE_COUNTERS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.ProviderTypes>|[Набор строк DBSCHEMA_PROVIDER_TYPES](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.SchemaRowsets>|[Набор строк DISCOVER_SCHEMA_ROWSETS](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sessions>|**DISCOVER_SESSIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sets>|[Набор строк MDSCHEMA_SETS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|AdomdConnection.Cubes[].NamedSets|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Tables>|[Набор строк DBSCHEMA_TABLES](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TablesInfo>|**DBSCHEMA_TABLES_INFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceColumns>|**DISCOVER_TRACE_COLUMNS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceDefinitionProviderInfo>|**DISCOVER_TRACE_DEFINITION_PROVIDERINFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceEventCategories>|**DISCOVER_TRACE_EVENT_CATEGORIES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Traces>|**DISCOVER_TRACES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Transactions>|**DISCOVER_TRANSACTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlaProperties>|[Набор строк DISCOVER_PROPERTIES](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlMetadata>|[Набор строк DISCOVER_XML_METADATA](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)||  
  
## <a name="see-also"></a>См. также:  
 [Программирование клиента ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Программирование клиента ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Наборы строк схемы служб Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
