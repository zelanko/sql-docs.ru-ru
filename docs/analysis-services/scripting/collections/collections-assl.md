---
title: "Коллекции (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- collections [Analysis Services Scripting Language]
- Analysis Services Scripting Language, collections
- ASSL, collections
ms.assetid: 072b8c6b-1550-4cab-ae64-ba0e3e60b059
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 68be246ab77c93a910a4d37b40808a42adecb8ae
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="collections-assl"></a>Коллекции (ASSL)
  В данном разделе приводится синтаксис и сведения об использовании каждого элемента, выступающего в роли коллекции в схеме ASSL.  
  
 Хотя схема ASSL содержит только элементы XML, с точки зрения разработчика, элементы, описанные в этом разделе относятся к коллекции объектов, такие как **измерения** и **кубов** коллекции.  
  
 Коллекции в основном являются коллекциями элементов-объектов, в которых существительное во множественном числе означают коллекцию (примеры, **кубы**), а коллекция содержит элементы, назначенному с помощью того же существительное в единственном числе (например,  **Куб**).  
  
 В некоторых случаях схема не соответствует этому общему правилу. Например **ClassifiedColumns** коллекция содержит **ClassifiedColumnID** элементов.  
  
 В других случаях коллекция содержит элементы, которые соответствуют свойствам объектов, а не объектам. Например **псевдонимы** коллекция содержит **псевдоним** свойства, каждый из которых является простым строковым значением.  
  
|Элемент|Description|  
|-------------|-----------------|  
|[Элемент Accounts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)|Содержит коллекцию типов учетных записей, которые определены в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент Actions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)|Содержит коллекцию действий для [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) или [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элемента.|  
|[Элемент AggregationDesigns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md)|Содержит коллекцию статистических схем, которые можно совместно использовать в разных секциях в базе данных.|  
|[Элемент AggregationInstances &#40; ASSL &#41;](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)|Содержит коллекцию экземпляров агрегатов, которые определены в [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) элемента.|  
|[Элемент aggregations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/aggregations-element-assl.md)|Содержит коллекцию агрегатов, определенных для [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) элемента.|  
|[Элемент AlgorithmParameters &#40; ASSL &#41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|Содержит коллекцию параметров для алгоритма, используемого в [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.|  
|[Элемент aliases &#40; ASSL &#41;](../../../analysis-services/scripting/collections/aliases-element-assl.md)|Содержит коллекцию элементов [псевдоним](../../../analysis-services/scripting/properties/alias-element-assl.md) элементы, связанные с [учетной записи](../../../analysis-services/scripting/objects/account-element-assl.md) элемент|  
|[Элемент AllMemberTranslations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)|Содержит коллекцию элементов [перевода](../../../analysis-services/scripting/objects/translation-element-assl.md) для заголовка элемента «все» [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.|  
|[Элемент Annotations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/annotations-element-assl.md)|Содержит коллекцию элементов [заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)|Содержит коллекцию элементов [сборки](../../../analysis-services/scripting/objects/assembly-element-assl.md) элементы, связанные с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемент или [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент AttributeAllMemberTranslations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/attributeallmembertranslations-element-assl.md)|Содержит коллекцию переводов для заголовка элемента «Все» в измерении.|  
|[Элемент AttributePermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|Содержит коллекцию разрешений атрибутов для отдельного [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента на конкретное измерение [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент AttributeRelationships &#40; ASSL &#41;](../../../analysis-services/scripting/collections/attributerelationships-element-assl.md)|Содержит коллекцию элементов [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) для атрибута.|  
|[Атрибуты элемента &#40; ASSL &#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)|Содержит коллекцию атрибутов для связанного измерения.|  
|[Элемент Blocks &#40; ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)|Содержит коллекцию блоков двоичных данных, которые представляют двоичное содержимое [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) элемента.|  
|[Элемент CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)|Содержит коллекцию элементов [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) элементы, связанные с [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) элемента.|  
|[Элемент Calculations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculations-element-assl.md)|Содержит коллекцию элементов [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md) элементы, связанные с [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элемента.|  
|[Элемент CellPermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/cellpermissions-element-assl.md)|Содержит коллекцию разрешений для ячеек в связанном [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент ClassifiedColumns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)|Содержит коллекцию связанных столбцов, классифицированных объектом [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md) элемента.|  
|[Элемент Columns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/columns-element-assl.md)|Содержит коллекцию столбцов, связанных с родительским элементом.|  
|[Элемент Commands &#40; ASSL &#41;](../../../analysis-services/scripting/collections/commands-element-assl.md)|Содержит коллекцию элементов [Command](../../../analysis-services/scripting/objects/command-element-assl.md) , связанных с элементом [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) .|  
|[Элемент CubePermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/cubepermissions-element-assl.md)|Содержит коллекцию разрешений, применимых к [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент Cubes &#40; ASSL &#41;](../../../analysis-services/scripting/collections/cubes-element-assl.md)|Содержит коллекцию элементов [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элементы, связанные с [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент DatabasePermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|Содержит коллекцию элементов [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md) элементы, связанные с [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент databases &#40; ASSL &#41;](../../../analysis-services/scripting/collections/databases-element-assl.md)|Содержит коллекцию элементов [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элементы, связанные с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.|  
|[Элемент DataSources &#40; ASSL &#41;](../../../analysis-services/scripting/collections/datasources-element-assl.md)|Содержит коллекцию элементов [DataSourcePermission](../../../analysis-services/scripting/objects/datasourcepermission-element-assl.md) элементы, связанные с [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) тип данных.|  
|[Элемент DataSourcePermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|Содержит коллекцию элементов [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) элементы, связанные с [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент DataSourceViews &#40; ASSL &#41;](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md)|Содержит коллекцию элементов [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md) элементы, связанные с [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент DimensionPermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md)|Содержит коллекцию разрешений, применимых к [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md) элемент или [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md) элемента.|  
|[Элемент Dimensions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/dimensions-element-assl.md)|Содержит коллекцию измерений, связанных с родительским элементом.|  
|[Элемент Events &#40; ASSL &#41;](../../../analysis-services/scripting/collections/events-element-assl.md)|Определяет коллекцию элементов событий, перехватываемых [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md).|  
|[Элемент Files &#40; ASSL &#41;](../../../analysis-services/scripting/collections/files-element-assl.md)|Содержит коллекцию элементов [файл](../../../analysis-services/scripting/objects/file-element-assl.md) элементов, составляющих [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) элемента.|  
|[Элемент ForeignKeyColumns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/foreignkeycolumns-element-assl.md)|Содержит коллекцию столбцов, которые определяют соединение с родительской таблицей для реляционного источника данных.|  
|[Элемент Groups &#40; ASSL &#41;](../../../analysis-services/scripting/collections/groups-element-assl.md)|Содержит коллекцию групп элементов, привязанных к атрибуту.|  
|[Элемент hierarchies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)|Содержит коллекцию элементов [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент IncrementalProcessingNotifications &#40; ASSL &#41;](../../../analysis-services/scripting/collections/incrementalprocessingnotifications-element-assl.md)|Содержит коллекцию элементов [IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md) элементы, которые содержат сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросах, необходимо выполнить, чтобы определить ход выполнения добавочной обработки.|  
|[Элемент KeyColumns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|Содержит коллекцию элементов [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) определений элементов для родительского объекта.|  
|[Элемент KPIs &#40; ASSL &#41;](../../../analysis-services/scripting/collections/kpis-element-assl.md)|Содержит коллекцию элементов [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md) элементы, связанные с родительским элементом.|  
|[Levels, элемент &#40; ASSL &#41;](../../../analysis-services/scripting/collections/levels-element-assl.md)|Содержит коллекцию элементов [уровень](../../../analysis-services/scripting/objects/level-element-assl.md) элементов в [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.|  
|[MdxScript, элемент &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)|Содержит коллекцию элементов [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) элементы, связанные с [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент MeasureGroups &#40; ASSL &#41;](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)|Содержит коллекцию элементов [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент Measures &#40; ASSL &#41;](../../../analysis-services/scripting/collections/measures-element-assl.md)|Содержит коллекцию элементов [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент Members &#40; ASSL &#41;](../../../analysis-services/scripting/collections/members-element-assl.md)|Содержит коллекцию элементов [Member](../../../analysis-services/scripting/objects/member-element-assl.md) для родительского элемента.|  
|[Элемент MiningModelPermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|Содержит коллекцию разрешений для [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.|  
|[Элемент MiningModels &#40; ASSL &#41;](../../../analysis-services/scripting/collections/miningmodels-element-assl.md)|Содержит коллекцию элементов [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элементы, связанные с [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md).|  
|[Элемент MiningStructurePermissions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)|Содержит коллекцию разрешений для [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента.|  
|[Элемент MiningStructures &#40; ASSL &#41;](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)|Содержит коллекцию элементов [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элементов в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент ModelingFlags &#40; ASSL &#41;](../../../analysis-services/scripting/collections/modelingflags-element-assl.md)|Содержит коллекцию элементов [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) для столбца в [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) или [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md).|  
|[Элемент NamingTemplateTranslations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)|Предоставляет коллекцию локализованных переводов для [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md) родителя [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md).|  
|[Элемент partitions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/partitions-element-assl.md)|Содержит коллекцию элементов [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) элементы, используемые методом [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) элемент или коллекцию привязок секций, которые составляют вне строки [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)элемент.|  
|[Элемент Perspectives &#40; ASSL &#41;](../../../analysis-services/scripting/collections/perspectives-element-assl.md)|Содержит коллекцию элементов [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элементы, связанные с [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент QueryNotifications &#40; ASSL &#41;](../../../analysis-services/scripting/collections/querynotifications-element-assl.md)|Содержит коллекцию элементов [QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md) элементы, которые содержат сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросах, необходимо выполнить, чтобы определить, был ли изменен источник данных.|  
|[Элемент ReportFormatParameters &#40; ASSL &#41;](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md)|Содержит коллекцию элементов [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md) для элемента [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) .|  
|[Элемент ReportParameters &#40; ASSL &#41;](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)|Содержит коллекцию элементов [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md) элементы для [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) элемента.|  
|[Элемент Roles &#40; ASSL &#41;](../../../analysis-services/scripting/collections/roles-element-assl.md)|Содержит коллекцию элементов [Role](../../../analysis-services/scripting/objects/role-element-assl.md) , определенных в родительском элементе.|  
|[Элемент ServerProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|Содержит коллекцию элементов [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) элементы, связанные с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.|  
|[Элемент TableNotifications &#40; ASSL &#41;](../../../analysis-services/scripting/collections/tablenotifications-element-assl.md)|Содержит коллекцию элементов [TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md) элементы, которые предоставляют сведения для [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о таблиц или представлений в источнике данных, которые были изменены.|  
|[Элемент traces &#40; ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)|Содержит коллекцию элементов [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) , связанных с элементом [Server](../../../analysis-services/scripting/objects/server-element-assl.md) .|  
|[Элемент Translations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/translations-element-assl.md)|Содержит коллекцию элементов [перевода](../../../analysis-services/scripting/objects/translation-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент UnknownMemberTranslations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/unknownmembertranslations-element-assl.md)|Содержит коллекцию переводов для заголовка элемента [UnknownMember](../../../analysis-services/scripting/properties/unknownmember-element-assl.md) элемента измерения.|  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services Scripting иерархия элементов XML языка &#40; ASSL &#41;](../../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
