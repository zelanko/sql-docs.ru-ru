---
title: Коллекции (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- collections [Analysis Services Scripting Language]
- Analysis Services Scripting Language, collections
- ASSL, collections
ms.assetid: 072b8c6b-1550-4cab-ae64-ba0e3e60b059
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a56b577f39c2b2f4ef7a4033203fcda9706d1370
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300994"
---
# <a name="collections-assl"></a>Коллекции (ASSL)
  В данном разделе приводится синтаксис и сведения об использовании каждого элемента, выступающего в роли коллекции в схеме ASSL.  
  
 Хотя схема ASSL содержит только XML-элементы, с точки зрения разработчика, описываемые в этом разделе элементы относятся к коллекциям объектов, таких как коллекции `Dimensions` и `Cubes`.  
  
 Коллекции в основном являются коллекциями элементов-объектов, которые будучи существительным во множественном числе означают коллекцию (например `Cubes`), а коллекция содержит элементы, обозначенные тем же существительным в единственном числе (например `Cube`).  
  
 В некоторых случаях схема не соответствует этому общему правилу. Например, коллекция `ClassifiedColumns` содержит элементы `ClassifiedColumnID`.  
  
 В других случаях коллекция содержит элементы, которые соответствуют свойствам объектов, а не объектам. Например, коллекция `Aliases` содержит свойства `Alias`, каждое из которых является простым строковым значением.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Учетные записи элемент &#40;ASSL&#41;](accounts-element-assl.md)|Содержит коллекцию типов учетных записей, которые определены в [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент Actions &#40;ASSL&#41;](actions-element-assl.md)|Содержит коллекцию действий для [куба](../objects/cube-element-assl.md) или [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Элемент AggregationDesigns &#40;ASSL&#41;](aggregationdesigns-element-assl.md)|Содержит коллекцию статистических схем, которые можно совместно использовать в разных секциях в базе данных.|  
|[Элемент AggregationInstances &#40;ASSL&#41;](aggregationinstances-element-assl.md)|Содержит коллекцию экземпляров агрегатов, которые определены в [секции](../objects/partition-element-assl.md) элемент.|  
|[Элемент aggregations &#40;ASSL&#41;](aggregations-element-assl.md)|Содержит коллекцию агрегатов, определенных для [AggregationDesign](../objects/aggregationdesign-element-assl.md) элемент.|  
|[Элемент AlgorithmParameters &#40;ASSL&#41;](algorithmparameters-element-assl.md)|Содержит коллекцию параметров для алгоритма, используемого в [MiningModel](../objects/miningmodel-element-assl.md) элемент.|  
|[Элемент aliases &#40;ASSL&#41;](aliases-element-assl.md)|Содержит коллекцию элементов [псевдоним](../properties/alias-element-assl.md) элементы, связанные с [учетной записи](../objects/account-element-assl.md) элемент|  
|[Элемент AllMemberTranslations &#40;ASSL&#41;](translations-element-assl.md)|Содержит коллекцию элементов [перевода](../objects/translation-element-assl.md) элементы для заголовка элемента «все» элемента [иерархии](../objects/hierarchy-element-assl.md) элемент.|  
|[Элемент Annotations &#40;ASSL&#41;](annotations-element-assl.md)|Содержит коллекцию элементов [заметки](../objects/annotation-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент Assemblies &#40;ASSL&#41;](assemblies-element-assl.md)|Содержит коллекцию элементов [сборки](../objects/assembly-element-assl.md) элементы, связанные с [Server](../objects/server-element-assl.md) элемент или [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент AttributeAllMemberTranslations &#40;ASSL&#41;](attributeallmembertranslations-element-assl.md)|Содержит коллекцию переводов для заголовка элемента «Все» в измерении.|  
|[Элемент AttributePermissions &#40;ASSL&#41;](attributepermissions-element-assl.md)|Содержит коллекцию разрешений атрибутов для отдельного [роли](../objects/role-element-assl.md) элемент с указанным измерением из [куба](../objects/cube-element-assl.md) элемент.|  
|[Элемент AttributeRelationships &#40;ASSL&#41;](relationships-element-assl.md)|Содержит коллекцию элементов [AttributeRelationship](../objects/attributerelationship-element-assl.md) элементов для атрибута.|  
|[Атрибуты элемента &#40;ASSL&#41;](attributes-element-assl.md)|Содержит коллекцию атрибутов для связанного измерения.|  
|[Блокирует элемент &#40;ASSL&#41;](blocks-element-assl.md)|Содержит коллекцию блоков двоичных данных, которые представляют двоичное содержимое [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) элемент.|  
|[Элемент CalculationProperties &#40;ASSL&#41;](calculationproperties-element-assl.md)|Содержит коллекцию элементов [CalculationProperty](../objects/calculationproperty-element-assl.md) элементы, связанные с [MdxScript](../objects/mdxscript-element-assl.md) элемент.|  
|[Элемент Calculations &#40;ASSL&#41;](calculations-element-assl.md)|Содержит коллекцию элементов [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) элементы, связанные с [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Элемент CellPermissions &#40;ASSL&#41;](cellpermissions-element-assl.md)|Содержит коллекцию разрешений для ячеек в связанном [куба](../objects/cube-element-assl.md) элемент.|  
|[Элемент ClassifiedColumns &#40;ASSL&#41;](columns-element-assl.md)|Содержит коллекцию связанных столбцов, классифицированных [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) элемент.|  
|[Элемент Columns &#40;ASSL&#41;](columns-element-assl.md)|Содержит коллекцию столбцов, связанных с родительским элементом.|  
|[Команды элемент &#40;ASSL&#41;](commands-element-assl.md)|Содержит коллекцию элементов [Command](../objects/command-element-assl.md) , связанных с элементом [MdxScript](../objects/mdxscript-element-assl.md) .|  
|[Элемент CubePermissions &#40;ASSL&#41;](cubepermissions-element-assl.md)|Содержит коллекцию разрешений, применимых к [куба](../objects/cube-element-assl.md) элемент.|  
|[Кубы элемент &#40;ASSL&#41;](cubes-element-assl.md)|Содержит коллекцию элементов [куба](../objects/cube-element-assl.md) элементы, связанные с [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент DatabasePermissions &#40;ASSL&#41;](databasepermissions-element-assl.md)|Содержит коллекцию элементов [DatabasePermission](../objects/databasepermission-element-assl.md) элементы, связанные с [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент databases &#40;ASSL&#41;](databases-element-assl.md)|Содержит коллекцию элементов [базы данных](../objects/database-element-assl.md) элементы, связанные с [Server](../objects/server-element-assl.md) элемент.|  
|[Элемент DataSources &#40;ASSL&#41;](datasources-element-assl.md)|Содержит коллекцию элементов [DataSourcePermission](../objects/datasourcepermission-element-assl.md) элементы, связанные с [DataSource](../data-type/datasource-data-type-assl.md) тип данных.|  
|[Элемент DataSourcePermissions &#40;ASSL&#41;](datasourcepermissions-element-assl.md)|Содержит коллекцию элементов [DataSource](../objects/datasource-element-assl.md) элементы, связанные с [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент DataSourceViews &#40;ASSL&#41;](datasourceviews-element-assl.md)|Содержит коллекцию элементов [DataSourceView](../objects/datasourceview-element-assl.md) элементы, связанные с [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент DimensionPermissions &#40;ASSL&#41;](dimensionpermissions-element-assl.md)|Содержит коллекцию разрешений, применимых к [измерения](../objects/dimension-element-assl.md) элемент или [CubePermission](../objects/cubepermission-element-assl.md) элемент.|  
|[Размеры элемента &#40;ASSL&#41;](dimensions-element-assl.md)|Содержит коллекцию измерений, связанных с родительским элементом.|  
|[Элемент Events &#40;ASSL&#41;](events-element-assl.md)|Определяет коллекцию элементов-событий фиксируемых [трассировки](../objects/trace-element-assl.md).|  
|[Файлы элемент &#40;ASSL&#41;](files-element-assl.md)|Содержит коллекцию элементов [файл](../objects/file-element-assl.md) элементы, составляющие [ClrAssembly](../data-type/assembly-data-type-assl.md) элемент.|  
|[Элемент ForeignKeyColumns &#40;ASSL&#41;](keycolumns-element-assl.md)|Содержит коллекцию столбцов, которые определяют соединение с родительской таблицей для реляционного источника данных.|  
|[Группирует элемент &#40;ASSL&#41;](groups-element-assl.md)|Содержит коллекцию групп элементов, привязанных к атрибуту.|  
|[Элемент hierarchies &#40;ASSL&#41;](hierarchies-element-assl.md)|Содержит коллекцию элементов [иерархии](../objects/hierarchy-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент IncrementalProcessingNotifications &#40;ASSL&#41;](incrementalprocessingnotifications-element-assl.md)|Содержит коллекцию элементов [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) элементы, которые содержат сведения, которые [ProactiveCaching](../objects/proactivecaching-element-assl.md) элемент о запросах, необходимо выполнить, чтобы узнать ход выполнения добавочной обработки.|  
|[Элемент KeyColumns &#40;ASSL&#41;](keycolumns-element-assl.md)|Содержит коллекцию элементов [KeyColumn](../objects/column-element-assl.md) определений элементов для родительского объекта.|  
|[Элемент KPIs &#40;ASSL&#41;](kpis-element-assl.md)|Содержит коллекцию элементов [ключевого показателя эффективности](../objects/kpi-element-assl.md) элементы, связанные с родительским элементом.|  
|[Уровни элемент &#40;ASSL&#41;](levels-element-assl.md)|Содержит коллекцию элементов [уровень](../objects/level-element-assl.md) элементов в [иерархии](../objects/hierarchy-element-assl.md) элемент.|  
|[Элемент MdxScripts &#40;ASSL&#41;](mdxscripts-element-assl.md)|Содержит коллекцию элементов [MdxScript](../objects/mdxscript-element-assl.md) элементы, связанные с [куба](../objects/cube-element-assl.md) элемент.|  
|[Элемент MeasureGroups &#40;ASSL&#41;](measuregroups-element-assl.md)|Содержит коллекцию элементов [MeasureGroup](../objects/group-element-assl.md) элементы, связанные с родительским элементом.|  
|[Измеряет элемент &#40;ASSL&#41;](measures-element-assl.md)|Содержит коллекцию элементов [мер](../objects/measure-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент Members &#40;ASSL&#41;](members-element-assl.md)|Содержит коллекцию элементов [Member](../objects/member-element-assl.md) для родительского элемента.|  
|[Элемент MiningModelPermissions &#40;ASSL&#41;](miningmodelpermissions-element-assl.md)|Содержит коллекцию разрешений для [MiningModel](../objects/miningmodel-element-assl.md) элемент.|  
|[Элемент MiningModels &#40;ASSL&#41;](miningmodels-element-assl.md)|Содержит коллекцию элементов [MiningModel](../objects/miningmodel-element-assl.md) элементы, связанные с [MiningStructure](../objects/miningstructure-element-assl.md).|  
|[Элемент MiningStructurePermissions &#40;ASSL&#41;](miningstructurepermissions-element-assl.md)|Содержит коллекцию разрешений на [MiningStructure](../objects/miningstructure-element-assl.md) элемент.|  
|[Элемент MiningStructures &#40;ASSL&#41;](miningstructures-element-assl.md)|Содержит коллекцию элементов [MiningStructure](../objects/miningstructure-element-assl.md) элементов в [базы данных](../objects/database-element-assl.md) элемент.|  
|[Элемент ModelingFlags &#40;ASSL&#41;](modelingflags-element-assl.md)|Содержит коллекцию элементов [ModelingFlag](../objects/modelingflag-element-assl.md) для столбца в [MiningStructure](../objects/miningstructure-element-assl.md) или [MiningModel](../objects/miningmodel-element-assl.md).|  
|[Элемент NamingTemplateTranslations &#40;ASSL&#41;](namingtemplatetranslations-element-assl.md)|Предоставляет коллекцию локализованных переводов для [NamingTemplate](../properties/namingtemplate-element-assl.md) родителя [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).|  
|[Разбивает элемент &#40;ASSL&#41;](partitions-element-assl.md)|Содержит коллекцию элементов [секции](../objects/partition-element-assl.md) элементы, используемые методом [MeasureGroup](../objects/group-element-assl.md) элемент или коллекцию привязок секций, которые составляют вне строки [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)элемент.|  
|[Элемент Perspectives &#40;ASSL&#41;](perspectives-element-assl.md)|Содержит коллекцию элементов [перспективы](../objects/perspective-element-assl.md) элементы, связанные с [куба](../objects/cube-element-assl.md) элемент.|  
|[Элемент QueryNotifications &#40;ASSL&#41;](querynotifications-element-assl.md)|Содержит коллекцию элементов [QueryNotification](../objects/querynotification-element-assl.md) элементы, которые содержат сведения, которые [ProactiveCaching](../objects/proactivecaching-element-assl.md) элемент о запросах, необходимо выполнить, чтобы определить, был ли изменен источник данных.|  
|[Элемент ReportFormatParameters &#40;ASSL&#41;](reportformatparameters-element-assl.md)|Содержит коллекцию элементов [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) для элемента [ReportAction](../data-type/action-data-type-assl.md) .|  
|[Элемент ReportParameters &#40;ASSL&#41;](reportparameters-element-assl.md)|Содержит коллекцию элементов [ReportParameter](../objects/reportparameter-element-assl.md) элементы для [ReportAction](../data-type/action-data-type-assl.md) элемент.|  
|[Элемент roles &#40;ASSL&#41;](roles-element-assl.md)|Содержит коллекцию элементов [Role](../objects/role-element-assl.md) , определенных в родительском элементе.|  
|[Элемент ServerProperties &#40;ASSL&#41;](serverproperties-element-assl.md)|Содержит коллекцию элементов [ServerProperty](../objects/serverproperty-element-assl.md) элементы, связанные с [Server](../objects/server-element-assl.md) элемент.|  
|[Элемент TableNotifications &#40;ASSL&#41;](tablenotifications-element-assl.md)|Содержит коллекцию элементов [TableNotification](../objects/tablenotification-element-assl.md) , которые предоставляют сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) о таблиц или представлений в источнике данных, которые были изменены.|  
|[Выполняет трассировку элемент &#40;ASSL&#41;](traces-element-assl.md)|Содержит коллекцию элементов [Trace](../objects/trace-element-assl.md) , связанных с элементом [Server](../objects/server-element-assl.md) .|  
|[Элемент Translations &#40;ASSL&#41;](translations-element-assl.md)|Содержит коллекцию элементов [перевода](../objects/translation-element-assl.md) элементы, связанные с родительским элементом.|  
|[Элемент UnknownMemberTranslations &#40;ASSL&#41;](unknownmembertranslations-element-assl.md)|Содержит коллекцию переводов для заголовка элемента [UnknownMember](../properties/unknownmember-element-assl.md) в измерении.|  
  
## <a name="see-also"></a>См. также  
 [Иерархия элементов XML для языка сценариев служб аналитики &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
