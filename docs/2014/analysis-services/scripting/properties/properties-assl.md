---
title: Свойства (ASSL) | Документы Microsoft
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
- properties [Analysis Services Scripting Language]
- Analysis Services Scripting Language, properties
- ASSL, properties
ms.assetid: 9a38cdc9-a210-421a-90e9-6391876765fa
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 72ec08342256fecbd63c791b6db6e343479bca65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102119"
---
# <a name="properties-assl"></a>Свойства (ASSL)
  В этом разделе справки содержатся сведения о синтаксисе и использовании каждого элемента, выступающего в качестве свойства объекта в схеме языка ASSL.  
  
 Хотя в схеме языка ASSL содержатся только элементы XML, но, с точки зрения разработчика, элементы, которые описываются в этом разделе, соответствуют свойствам, описывающим объекты.  
  
 Свойства — это элементы конечного уровня схемы языка ASSL, и они не могут иметь дочерние элементы или элементы, которые соответствуют их собственным свойствам.  
  
 В редких случаях конечный элемент в схеме, который выглядит как свойство, классифицируется как объект, поскольку тип элемента является типом объекта. Например, `Source` объекта `Dimension` имеет тип `DimensionBinding`.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Доступ к элементу &#40;ASSL&#41;](access-element-assl.md)|Указывает уровень доступа для [CellPermission](../objects/cellpermission-element-assl.md) элемента.|  
|[Учетная запись элемент &#40;ImpersonationInfo&#41; &#40;ASSL&#41;](account-element-impersonationinfo-assl.md)|Содержит имя учетной записи пользователя для [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) тип данных.|  
|[Элемент AccountType &#40;ASSL&#41;](accounttype-element-assl.md)|Содержит имя типа учетной записи, определенные в [базы данных](../objects/database-element-assl.md) элемента.|  
|[Элемент ActionID &#40;ASSL&#41;](id-element-assl.md)|Содержит имя [действия](../objects/action-element-assl.md) элемент, определенный на [куба](../objects/cube-element-assl.md) элемент, который доступен в [перспективы](../objects/perspective-element-assl.md) элемент как [PerspectiveAction](../data-type/action-data-type-assl.md) элемента.|  
|[Элемент Administer &#40;ASSL&#41;](administer-element-assl.md)|Показывает, включает ли связанное разрешение право администрировать элемент `Database`.|  
|[Элемент AggregateFunction &#40;ASSL&#41;](aggregatefunction-element-assl.md)|Определяет тип агрегатной функции, используемой [мер](../objects/measure-element-assl.md) элемента.|  
|[Элемент AggregationDesignID &#40;ASSL&#41;](aggregationdesignid-element-assl.md)|Идентифицирует [AggregationDesign](../objects/aggregationdesign-element-assl.md) элемента, связанного с [секции](../objects/partition-element-assl.md) элемента.|  
|[Элемент AggregationFunction &#40;ASSL&#41;](aggregationfunction-element-assl.md)|Содержит статистическую функцию, используемую для типа счета.|  
|[Элемент AggregationID &#40;ASSL&#41;](aggregationid-element-assl.md)|Идентифицирует определение агрегата из элемента `AggregationDesign`, который был использован для создания экземпляра агрегата.|  
|[Элемент AggregationInstanceSource &#40;ASSL&#41;](aggregationinstancesource-element-assl.md)|Определяет источник данных для определяемых пользователем экземпляров агрегатов, привязанных к элементу `Partition`.|  
|[Элемент AggregationPrefix &#40;ASSL&#41;](aggregationprefix-element-assl.md)|Определяет общий префикс для имен агрегатов везде в связанном родительском элементе.|  
|[Элемент AggregationStorage &#40;ASSL&#41;](aggregationstorage-element-assl.md)|Определяет метод хранения для агрегатов.|  
|[Элемент AggregationType &#40;ASSL&#41;](aggregationtype-element-assl.md)|Определяет тип агрегата, сохраненного элементом `Partition`.|  
|[Элемент AggregationUsage &#40;ASSL&#41;](aggregationusage-element-assl.md)|Элементы управления как конструктор статистических схем в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] статистических схем.|  
|[Элемент Algorithm &#40;ASSL&#41;](algorithm-element-assl.md)|Определяет алгоритм, используемый [MiningModel](../objects/miningmodel-element-assl.md) элемента.|  
|[Элемент alias &#40;ASSL&#41;](alias-element-assl.md)|Определяет псевдоним для [учетной записи](../objects/account-element-assl.md) элемента.|  
|[Элемент AllMemberAggregationUsage &#40;ASSL&#41;](allmemberaggregationusage-element-assl.md)|Управляет тем, как конструктор статистических схем в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] конструирует агрегаты.|  
|[Элемент AllMemberName &#40;ASSL&#41;](name-element-assl.md)|Содержит заголовок на языке по умолчанию для элемента «все» [иерархии](../objects/hierarchy-element-assl.md) элемента.|  
|[Элемент AllowBrowsing &#40;ASSL&#41;](allowbrowsing-element-assl.md)|Определяет ли члены [роли](../objects/role-element-assl.md) элемент иметь разрешение на просмотр `MiningModel` элемент.|  
|[Элемент AllowDrillThrough &#40;ASSL&#41;](allowdrillthrough-element-assl.md)|Определяет, разрешена ли детализация для родительского элемента.|  
|[Элемент AllowDuplicateNames &#40;ASSL&#41;](allowduplicatenames-element-assl.md)|Определяет, допустимы ли в элементе `Hierarchy` повторяющиеся имена.|  
|[Элемент AllowedSet &#40;ASSL&#41;](allowedset-element-assl.md)|Содержит выражение набора, определяющее набор предоставленных разрешений для элемента `Role` атрибута.|  
|[Элемент Application &#40;ASSL&#41;](application-element-assl.md)|Определяет приложение, связанное с элементом `Action`.|  
|[Элемент AssociatedMeasureGroupID &#40;ASSL&#41;](measuregroupid-element-assl.md)|Содержит идентификатор (ID) [MeasureGroup](../objects/group-element-assl.md) элемента, связанного с [CalculationProperty](../objects/calculationproperty-element-assl.md) элемент или [ключевого показателя эффективности](../objects/kpi-element-assl.md) элемента.|  
|[Элемент AttributeAllMemberName &#40;ASSL&#41;](attributeallmembername-element-assl.md)|Содержит заголовок на языке по умолчанию для элемента «Все» измерения.|  
|[Элемент AttributeHierarchyDisplayFolder &#40;ASSL&#41;](displayfolder-element-assl.md)|Определяет папку, в которой отображается связанная иерархия атрибутов.|  
|[Элемент AttributeHierarchyEnabled &#40;ASSL&#41;](enabled-element-assl.md)|Определяет, включена ли иерархия атрибутов для атрибута.|  
|[Элемент AttributeHierarchyOptimizedState &#40;ASSL&#41;](state-element-assl.md)|Определяет уровень оптимизации иерархии атрибутов.|  
|[Элемент AttributeHierarchyOrdered &#40;ASSL&#41;](attributehierarchyordered-element-assl.md)|Определяет упорядоченность связанной иерархии атрибутов.|  
|[Элемент AttributeHierarchyVisible &#40;ASSL&#41;](visible-element-assl.md)|Определяет, является ли иерархия атрибутов видимой для клиентских приложений.|  
|[Элемент AttributeID &#40;ASSL&#41;](attributeid-element-assl.md)|Содержит идентификатор атрибута, связанного с родительским элементом.|  
|[Элемент Audit &#40;ASSL&#41;](audit-element-assl.md)|Указывает, что [трассировки](../objects/trace-element-assl.md) элемент не может удалять любые события, даже если это приводит к снижению производительности сервера.|  
|[Элемент AutoRestart &#40;ASSL&#41;](autorestart-element-assl.md)|Определяет, должен ли элемент `Trace` автоматически перезапускаться в случае, если служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] останавливается или перезапускается.|  
|[Элемент BackColor &#40;ASSL&#41;](backcolor-element-assl.md)|Описывает связанные с цветом характеристики отображения родительского элемента.|  
|[Элемент CacheMode &#40;ASSL&#41;](cachemode-element-assl.md)|Определяет механизм кэширования, который используется для обучающих данных, полученных при обработке структуры интеллектуального анализа данных.|  
|[Элемент CalculationReference &#40;ASSL&#41;](calculationreference-element-assl.md)|Содержит имя именованного набора или вычисляемой ячейки, на которую ссылается элемент `CalculationProperty`.|  
|[Элемент CalculationType &#40;ASSL&#41;](calculationtype-element-assl.md)|Описывает тип вычисления, определенного в связанном элементе `CalculationProperty`.|  
|[Элемент CalendarEndDate &#40;ASSL&#41;](calendarenddate-element-assl.md)|Определяет конечную дату календарного периода для [TimeBinding](../data-type/binding-data-type-assl.md) элемента.|  
|[Элемент CalendarLanguage &#40;ASSL&#41;](language-element-assl.md)|Определяет язык календаря, используемый в элементе `TimeBinding`.|  
|[Элемент CalendarStartDate &#40;ASSL&#41;](calendarstartdate-element-assl.md)|Определяет начальную дату календарного периода для элемента `TimeBinding`.|  
|[Заголовок элемента &#40;ASSL&#41;](caption-element-assl.md)|Содержит заголовок для связанного родительского элемента.|  
|[Элемент CaptionIsMdx &#40;ASSL&#41;](captionismdx-element-assl.md)|Определяет, является ли заголовок элемента `Action` многомерным выражением.|  
|[Элемент Cardinality &#40;ASSL&#41;](cardinality-element-assl.md)|Указывает количество элементов связи, описываемой элементом [AttributeRelationship](../objects/attributerelationship-element-assl.md) или [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md).|  
|[Элемент CaseCubeDimensionID &#40;ASSL&#41;](dimensionid-element-assl.md)|Содержит идентификатор измерения куба, который связывает измерение интеллектуального анализа данных с группой мер.|  
|[Элемент ClassifiedColumnID &#40;ASSL&#41;](classifiedcolumnid-element-assl.md)|Содержит идентификатор связанного столбца, классифицированного по [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) элемента.|  
|[Элемент collation &#40;ASSL&#41;](collation-element-assl.md)|Задает параметры сортировки, применяемые в родительском элементе.|  
|[Элемент ColumnID &#40;ColumnBinding&#41; &#40;ASSL&#41;](columnid-element-columnbinding-assl.md)|Содержит идентификатор столбца в таблице, к которому привязан элемент данных.|  
|[Элемент ColumnID &#40;EventColumn&#41; &#40;ASSL&#41;](columnid-element-eventcolumn-assl.md)|Содержит идентификатор столбца данных, которые будут захвачены для события как часть элемента `Trace`.|  
|[Условие элемент &#40;ASSL&#41;](condition-element-assl.md)|Содержит многомерное выражение, определяющее, входит ли цель в область применения родительского элемента `Action`.|  
|[Элемент ConnectionString &#40;ASSL&#41;](connectionstring-element-assl.md)|Содержит зашифрованную строку подключения для [DataSource](../objects/datasource-element-assl.md) элемента.|  
|[Элемент ConnectionStringSecurity &#40;ASSL&#41;](connectionstringsecurity-element-assl.md)|Указывает, исключается ли пароль пользователя из строки подключения для источника данных в целях безопасности.|  
|[Элемент содержимого &#40;ASSL&#41;](content-element-assl.md)|Описывает содержимое столбца в [MiningStructure](../objects/miningstructure-element-assl.md) элемента.|  
|[Элемент CreatedTimestamp &#40;ASSL&#41;](createdtimestamp-element-assl.md)|Содержит отметку времени только для чтения с временем создания родительского элемента.|  
|[Элемент CubeDimensionID &#40;ASSL&#41;](cubedimensionid-element-assl.md)|Идентифицирует [CubeDimension](../data-type/cubedimension-data-type-assl.md) элемент, связанный с родительским элементом.|  
|[Элемент CubeID &#40;ASSL&#41;](cubeid-element-assl.md)|Идентифицирует `Cube` элемента, связанного с [привязки](../data-type/binding-data-type-assl.md) элемента.|  
|[Элемент CurrentStorageMode &#40;ASSL&#41;](storagemode-element-assl.md)|Определяет текущий режим хранения для родительского элемента.|  
|[Элемент CurrentTimeMember &#40;ASSL&#41;](../objects/member-element-assl.md)|Определяет текущий элемент измерения времени, связанный с элементом `Kpi`.|  
|[Элемент DataAggregation &#40;ASSL&#41;](../objects/aggregation-element-assl.md)|Определяет, может ли экземпляр выполнять статистическое вычисление материализованных или кэшированных данных для элемента `MeasureGroup`.|  
|[Элемент DatabaseID &#40;ASSL&#41;](databaseid-element-assl.md)|Определяет элемент `Database`, связанный с внешним элементом `Binding`.|  
|[Элемент DataSize &#40;ASSL&#41;](datasize-element-assl.md)|Содержит размер в байтах [DataItem](../data-type/dataitem-data-type-assl.md) элемента.|  
|[Элемент DataSourceID &#40;ASSL&#41;](datasourceid-element-assl.md)|Определяет элемент `DataSource`, связанный с родительским элементом.|  
|[Элемент DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Содержит сведения, определяющие поведение при олицетворении во время соединения с источником данных для элемента `Database`.|  
|[Элемент DataSourceViewID &#40;ASSL&#41;](datasourceviewid-element-assl.md)|Идентифицирует [DataSourceView](../objects/datasourceview-element-assl.md) элемента, связанного с `Binding` родительского элемента.|  
|[Элемент DataType &#40;ASSL&#41;](datatype-element-assl.md)|Определяет тип данных связанного элемента.|  
|[Элемент DbSchemaName &#40;ASSL&#41;](dbschemaname-element-assl.md)|Содержит имя схемы, используемой родительским элементом в таблице, указанной [DbTableName](dbtablename-element-assl.md) элемента.|  
|[Элемент DbTableName &#40;ASSL&#41;](dbtablename-element-assl.md)|Содержит имя таблицы, к которой привязан родительский элемент.|  
|[По умолчанию элемент &#40;ASSL&#41;](default-element-assl.md)|Определяет, является ли действие `DrillThroughAction` действием детализации по умолчанию.|  
|[Элемент DefaultMeasure &#40;ASSL&#41;](defaultmeasure-element-assl.md)|Содержит многомерное выражение, определяющее меру по умолчанию для элемента `Cube` или `Perspective`.|  
|[Элемент DefaultMember &#40;ASSL&#41;](defaultmember-element-assl.md)|Содержит многомерное выражение, определяющее элемент по умолчанию родительского элемента.|  
|[Элемент DefaultScript &#40;ASSL&#41;](defaultscript-element-assl.md)|Определяет значение по умолчанию [MdxScript](../objects/mdxscript-element-assl.md) элемент в [MdxScripts](../collections/mdxscripts-element-assl.md) коллекции.|  
|[Элемент DefaultValue &#40;ASSL&#41;](value-element-assl.md)|Значение по умолчанию только для чтения связанного [ServerProperty](../objects/serverproperty-element-assl.md) элемента.|  
|[Элемент DeniedSet &#40;ASSL&#41;](deniedset-element-assl.md)|Содержит выражение набора, определяющее список разрешений, которые отклоняются для связанного атрибута.|  
|[Элемент DependsOnDimensionID &#40;ASSL&#41;](dependsondimensionid-element-assl.md)|Содержит идентификатор другого измерения, от которого зависит родительское измерение.|  
|[Элемент Description &#40;ASSL&#41;](description-element-assl.md)|Содержит описание родительского элемента.|  
|[Элемент DimensionID &#40;ASSL&#41;](dimensionid-element-assl.md)|Содержит идентификатор измерения.|  
|[Элемент DiscretizationBucketCount &#40;ASSL&#41;](discretizationbucketcount-element-assl.md)|Содержит количество сегментов дискретизации.|  
|[Элемент DiscretizationMethod &#40;ASSL&#41;](discretizationmethod-element-assl.md)|Определяет метод дискретизации.|  
|[Элемент DisplayFlag &#40;ASSL&#41;](displayflag-element-assl.md)|Содержит доступную только для чтения подсказку, которая указывает, должны ли компоненты пользовательского интерфейса показывать связанный элемент `ServerProperty`.|  
|[Элемент DisplayFolder &#40;ASSL&#41;](displayfolder-element-assl.md)|Указывает папку, в которой должен отображаться родительский элемент. В приложениях служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для разработчиков и администраторов могут поддерживаться папки отображения для визуальной классификации нескольких элементов.|  
|[Элемент Distribution &#40;ASSL&#41;](distribution-element-assl.md)|Содержит зависящее от поставщика значение, которое описывает, как распределены скалярные значения в столбце элемента `MiningStructure`.|  
|[Элемент Edition &#40;ASSL&#41;](edition-element-assl.md)|Содержит доступный только для чтения выпуск экземпляра [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] представленный [сервера](../objects/server-element-assl.md) элемента.|  
|[Включить элемент &#40;ASSL&#41;](enabled-element-assl.md)|Указывает, включен ли родительский элемент.|  
|[Элемент EndOfData &#40;ASSL&#41;](../objects/data-element-assl.md)|Указывает конец данных, полученных от [PushedDataSource](../data-type/datasource-data-type-assl.md) элемента.|  
|[Элемент EstimatedCount &#40;ASSL&#41;](estimatedcount-element-assl.md)|Содержит предполагаемое количество элементов атрибута.|  
|[Элемент EstimatedPerformanceGain &#40;ASSL&#41;](estimatedperformancegain-element-assl.md)|Содержит процентное значение (только для чтения) ожидаемого прироста производительности для секции.|  
|[Элемент EstimatedRows &#40;ASSL&#41;](estimatedrows-element-assl.md)|Содержит ожидаемое число строк, представленных родительским элементом.|  
|[Элемент EstimatedSize &#40;ASSL&#41;](estimatedsize-element-assl.md)|Содержит предполагаемый, доступный только для чтения размер родительского элемента в байтах.|  
|[Элемент EventID &#40;ASSL&#41;](eventid-element-assl.md)|Уникально идентифицирует [событий](../objects/event-element-assl.md) элемент, который будет захвачен как часть `Trace` элемента.|  
|[Элемент выражения &#40;ASSL&#41;](expression-element-assl.md)|Содержит многомерное выражение, определяющее содержимое родительского элемента.|  
|[Элемент filter &#40;привязки&#41; &#40;ASSL&#41;](filter-element-binding-assl.md)|Содержит многомерное выражение, которое фильтрует содержимое родительского элемента.|  
|[Элемент filter &#40;трассировки&#41; &#40;ASSL&#41;](filter-element-trace-assl.md)|Содержит фрагмент XML-документа, который описывает фильтр `Trace`.|  
|[Элемент FirstDayOfWeek &#40;ASSL&#41;](firstdayofweek-element-assl.md)|Определяет первый день недели для элемента `TimeBinding`.|  
|[Элемент FiscalFirstDayOfMonth &#40;ASSL&#41;](fiscalfirstdayofmonth-element-assl.md)|Определяет первый день финансового месяца для элемента `TimeBinding`.|  
|[Элемент FiscalFirstMonth &#40;ASSL&#41;](fiscalfirstmonth-element-assl.md)|Определяет первый месяц финансового периода для элемента `TimeBinding`.|  
|[Элемент FiscalYearName &#40;ASSL&#41;](fiscalyearname-element-assl.md)|Определяет соглашение об именах для имени финансового года для элемента `TimeBinding`.|  
|[Элемент FontFlags &#40;ASSL&#41;](fontflags-element-assl.md)|Описывает связанные со шрифтами характеристики отображения родительского элемента `CalculationProperty` или `Measure`.|  
|[Элемент FontName &#40;ASSL&#41;](fontname-element-assl.md)|Описывает связанные со шрифтами характеристики отображения родительского элемента `CalculationProperty` или `Measure`.|  
|[Элемент FontSize &#40;ASSL&#41;](fontsize-element-assl.md)|Описывает связанные со шрифтами характеристики отображения родительского элемента `CalculationProperty` или `Measure`.|  
|[Элемент ForceRebuildInterval &#40;ASSL&#41;](forcerebuildinterval-element-assl.md)|Определяет время (начиная с момента, когда становится доступным новый образ многомерного OLAP (MOLAP)), через которое безусловно начинается операция создания образа MOLAP.|  
|[Элемент ForeColor &#40;ASSL&#41;](forecolor-element-assl.md)|Описывает цветовые характеристики отображения родительского элемента `CalculationProperty` или `Measure`.|  
|[Форматирование элемента &#40;ASSL&#41;](format-element-assl.md)|Содержит требуемый формат элемента `DataItem`.|  
|[Элемент FormatString &#40;ASSL&#41;](formatstring-element-assl.md)|Описывает формат отображения элемента `CalculationProperty` или `Measure`.|  
|[Элемент Goal &#40;ASSL&#41;](goal-element-assl.md)|Определяет цель элемента `Kpi`.|  
|[Элемент GranularityAttributeID &#40;ASSL&#41;](granularityattributeid-element-assl.md)|Содержит идентификатор атрибута, связанного с родительским объектом [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md) тип данных.|  
|[Элемент HideMemberIf &#40;ASSL&#41;](hidememberif-element-assl.md)|Указывает, необходимо ли и когда необходимо скрывать элемент уровня от клиентских приложений.|  
|[Элемент HierarchyID &#40;ASSL&#41;](hierarchyid-element-assl.md)|Содержит идентификатор для [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md), или [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md) элемента.|  
|[Элемент HierarchyUniqueNameStyle &#40;ASSL&#41;](hierarchyuniquenamestyle-element-assl.md)|Определяет правила формирования уникальных имен для иерархий, содержащихся в элементе `CubeDimension`.|  
|[Элемент ID &#40;ASSL&#41;](id-element-assl.md)|Содержит уникальный идентификатор родительского элемента.|  
|[Элемент IgnoreUnrelatedDimensions &#40;ASSL&#41;](../collections/dimensions-element-assl.md)|Определяет, будут ли несвязанные измерения принудительно перемещаться на верхний уровень, если элементы измерений, не связанных с группой мер, включаются в запрос.|  
|[Элемент ImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Содержит данные, которые используются для задания режима олицетворения при доступе или исполнении сборки.|  
|[Элемент ImpersonationInfoSecurity &#40;ASSL&#41;](impersonationinfosecurity-element-assl.md)|Содержит доступное только для чтения значение, которое показывает, вносились ли изменения в учетные данные безопасности, предоставленные в типе данных `ImpersonationInfo`.|  
|[Элемент ImpersonationMode &#40;ASSL&#41;](impersonationmode-element-assl.md)|Содержит значение, указывающее метод олицетворения для элементов, производных от типа данных `ImpersonationInfo`.|  
|[Элемент InstanceSelection &#40;ASSL&#41;](instanceselection-element-assl.md)|Предоставляет указания для клиентских приложений о том, как следует отображать список элементов на основе предполагаемого количества элементов в списке.|  
|[Элемент IntermediateCubeDimensionID &#40;ASSL&#41;](intermediatecubedimensionid-element-assl.md)|Содержит идентификатор измерения, который связывает ссылочное измерение с группой мер.|  
|[Элемент IntermediateGranularityAttributeID &#40;ASSL&#41;](intermediategranularityattributeid-element-assl.md)|Содержит идентификатор атрибута гранулярности в промежуточном измерении куба, который связывает ссылочное измерение с промежуточным.|  
|[Элемент InvalidXmlCharacters &#40;ASSL&#41;](invalidxmlcharacters-element-assl.md)|Определяет метод обработки неправильных символов XML в исходных данных.|  
|[Элемент invocation &#40;ASSL&#41;](invocation-element-assl.md)|Указывает способ вызова `Action`.|  
|[Элемент IsAggregatable &#40;ASSL&#41;](isaggregatable-element-assl.md)|Указывает, является ли значения [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) элемент может быть статистически вычислена.|  
|[Элемент IsKey &#40;ASSL&#41;](iskey-element-assl.md)|Показывает, предоставляет ли столбец ключ для варианта в элементе `MiningStructure`.|  
|[Элемент isolation &#40;ASSL&#41;](isolation-element-assl.md)|Указывает уровень изоляции для элемента, который является производным от [DataSource](../data-type/datasource-data-type-assl.md) тип данных.|  
|[Элемент KeyDuplicate &#40;ASSL&#41;](keyduplicate-element-assl.md)|Определяет, как службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] будут обрабатывать ошибку повторяющихся ключей, если она возникнет во время работы.|  
|[Элемент KeyErrorAction &#40;ASSL&#41;](keyerroraction-element-assl.md)|Задает действие, предпринимаемое службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] при возникновении ошибки ключа.|  
|[Элемент KeyErrorLimit &#40;ASSL&#41;](keyerrorlimit-element-assl.md)|Содержит число допустимых во время обработки ошибок.|  
|[Элемент KeyErrorLimitAction &#40;ASSL&#41;](keyerrorlimitaction-element-assl.md)|Указывает действие, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] предпринимать, когда количество ошибок ключа, который указывается в [KeyErrorLimit](keyerrorlimit-element-assl.md) достигнут элемент.|  
|[Элемент KeyErrorLogFile &#40;ASSL&#41;](../objects/file-element-assl.md)|Содержит имя файла для ведения журнала ошибок обработки.|  
|[Элемент KeyNotFound &#40;ASSL&#41;](keynotfound-element-assl.md)|Определяет поведение служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] при обнаружении ошибки ссылочной целостности.|  
|[Элемент KeyUniquenessGuarantee &#40;ASSL&#41;](keyuniquenessguarantee-element-assl.md)|Определяет, гарантируется ли правильность связи между ключом атрибута и его именем и связи со связанными атрибутами.|  
|[Элемент KpiID &#40;ASSL&#41;](kpiid-element-assl.md)|Содержит идентификатор, связывающий элемент `Kpi` с элементом `Perspective`.|  
|[Элемент языка &#40;ASSL&#41;](language-element-assl.md)|Содержит идентификатор языка родительского элемента.|  
|[Элемент LastProcessed &#40;ASSL&#41;](lastprocessed-element-assl.md)|Содержит отметку времени только для чтения, которая указывает время последней обработки базы данных, содержащей родительский элемент.|  
|[Элемент LastSchemaUpdate &#40;ASSL&#41;](lastschemaupdate-element-assl.md)|Содержит отметку времени только для чтения с временем обновления метаданных родительского элемента.|  
|[Элемент LastUpdate &#40;ASSL&#41;](lastupdate-element-assl.md)|Содержит доступную только для чтения отметку времени, показывающую время последнего изменения связанного элемента `Database` или любых содержащихся в нем главных объектов.|  
|[Элемент latency &#40;ASSL&#41;](latency-element-assl.md)|Определяет время ожидания, которое проходит от момента самого раннего уведомления до момента удаления образов MOLAP.|  
|[Элемент LogFileAppend &#40;ASSL&#41;](logfileappend-element-assl.md)|Определяет, будет ли элемент `Trace` присоединять свой выход ведения журнала к существующему файлу журнала или перезаписывать его.|  
|[Элемент LogFileName &#40;ASSL&#41;](logfilename-element-assl.md)|Содержит имя файла журнала элемента `Trace`.|  
|[Элемент LogFileRollover &#40;ASSL&#41;](logfilerollover-element-assl.md)|Указывает, будет ли протоколирование данных `Trace` должен продолжаться выходные данные в новый файл или при достижении максимального размера файла журнала, указанного в [LogFileSize](logfilesize-element-assl.md) достигается.|  
|[Элемент LogFileSize &#40;ASSL&#41;](logfilesize-element-assl.md)|Определяет максимальный размер файла журнала в мегабайтах.|  
|[Элемент ManagedProvider &#40;ASSL&#41;](managedprovider-element-assl.md)|Содержит имя управляемого поставщика, используемого элементом, производным от типа данных `DataSource`.|  
|[Элемент ManufacturingExtraMonthQuarter &#40;ASSL&#41;](manufacturingextramonthquarter-element-assl.md)|Определяет месяц производственного периода, которому присваивается дополнительный месяц для элемента `TimeBinding`.|  
|[Элемент ManufacturingFirstMonth &#40;ASSL&#41;](manufacturingfirstmonth-element-assl.md)|Определяет первый производственный месяц для элемента `TimeBinding`.|  
|[Элемент ManufacturingFirstWeekOfMonth &#40;ASSL&#41;](manufacturingfirstweekofmonth-element-assl.md)|Определяет первую неделю производственного месяца для элемента `TimeBinding`.|  
|[Элемент MasterDatasourceID &#40;ASSL&#41;](masterdatasourceid-element-assl.md)|Содержит идентификатор основного источника данных для элемента `Database`.|  
|[Элемент Materialization &#40;ASSL&#41;](materialization-element-assl.md)|Указывает тип связи между группой мер и ссылочным измерением.|  
|[Элемент MaxActiveConnections &#40;ASSL&#41;](maxactiveconnections-element-assl.md)|Содержит максимальное число одновременных соединений, которое допускается элементом, производным от типа данных `DataSource`.|  
|[Элемент MdxMissingMemberMode &#40;ASSL&#41;](mdxmissingmembermode-element-assl.md)|Определяет, как обрабатываются пропущенные элементы для инструкций многомерных выражений.|  
|[Элемент MeasureExpression &#40;ASSL&#41;](measureexpression-element-assl.md)|Содержит многомерное выражение, определяющее меру.|  
|[Элемент MeasureGroupID &#40;ASSL&#41;](measuregroupid-element-assl.md)|Связывает элемент `MeasureGroup` с родительским элементом, привязкой или внешней привязкой.|  
|[Элемент MeasureID &#40;ASSL&#41;](measureid-element-assl.md)|Связывает элемент `Measure` с родительским элементом.|  
|[Элемент MeasureQualificaton &#40;ASSL&#41;](measurequalificaton-element-assl.md)|Определяет, применяется ли префикс к мерам в элементе `MeasureGroup`.|  
|[Элемент MemberNamesUnique &#40;ASSL&#41;](membernamesunique-element-assl.md)|Определяет, должны ли быть уникальными имена элементов для родительского элемента.|  
|[Элемент MemberUniqueNameStyle &#40;ASSL&#41;](memberuniquenamestyle-element-assl.md)|Определяет правила формирования уникальных имен для элементов иерархий, содержащихся в элементе `CubeDimension`.|  
|[Элемент MembersWithData &#40;ASSL&#41;](memberswithdata-element-assl.md)|Определяет, следует ли отображать элементы данных для неконечных элементов в родительском атрибуте.|  
|[Элемент MembersWithDataCaption &#40;ASSL&#41;](memberswithdatacaption-element-assl.md)|Задает шаблонную строку, применяемую при создании заголовков для сформированных системой элементов данных.|  
|[Элемент MimeType &#40;ASSL&#41;](mimetype-element-assl.md)|Содержит тип MIME, если он применим, для данных, представленных родительским элементом `DataItem`.|  
|[Элемент MiningModelID &#40;ASSL&#41;](miningmodelid-element-assl.md)|Связывает модель интеллектуального анализа данных с измерением интеллектуального анализа данных.|  
|[Элемент Name &#40;ASSL&#41;](name-element-assl.md)|Содержит имя родительского элемента.|  
|[Элемент NamingTemplate &#40;ASSL&#41;](namingtemplate-element-assl.md)|Определяет, как именуются уровни в иерархии типа «родители-потомки», созданной из родительского элемента `DimensionAttribute`.|  
|[Элемент NonEmptyBehavior &#40;ASSL&#41;](nonemptybehavior-element-assl.md)|Определяет установленное поведение, связанное с родителем элемента `CalculationProperty`.|  
|[Элемент NotificationTechnique &#40;ASSL&#41;](notificationtechnique-element-assl.md)|Указывает, является ли [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или внешним клиентским приложением обрабатывает уведомления.|  
|[Элемент NullKeyConvertedToUnknown &#40;ASSL&#41;](nullkeyconvertedtounknown-element-assl.md)|Определяет действие, которое следует выполнять при возникновении ошибки преобразования значения NULL.|  
|[Элемент NullKeyNotAllowed &#40;ASSL&#41;](nullkeynotallowed-element-assl.md)|Определяет, как ядро обработки служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] будет обрабатывать ошибку ключа NULL.|  
|[Элемент NullProcessing &#40;ASSL&#41;](nullprocessing-element-assl.md)|Определяет способ обработки значений NULL.|  
|[Элемент OnlineMode &#40;ASSL&#41;](onlinemode-element-assl.md)|Определяет, возвращается ли база данных в состояние «в сети» сразу в начале перестройки кэша или только после окончания перестройки.|  
|[Элемент OptimizedState &#40;ASSL&#41;](state-element-assl.md)|Определяет уровень оптимизации, применяемый к иерархии.|  
|[Элемент optionality &#40;ASSL&#41;](optionality-element-assl.md)|Показывает необязательность членов элемента `AttributeRelationship`.|  
|[Элемент OrderBy &#40;ASSL&#41;](orderby-element-assl.md)|Описывает, как упорядочивать элементы, содержащиеся в атрибуте.|  
|[Элемент OrderByAttributeID &#40;ASSL&#41;](orderbyattributeid-element-assl.md)|Определяет другой атрибут, по которому выполняется упорядочивание элементов атрибута [измерения](../data-type/dimensionattribute-data-type-assl.md) атрибута.|  
|[Элемент Ordinal &#40;ASSL&#41;](ordinal-element-assl.md)|Определяет порядковый номер, к которому следует выполнять привязку в таких коллекциях, как коллекции ключей и переводов.|  
|[Элемент OverrideBehavior &#40;ASSL&#41;](overridebehavior-element-assl.md)|Указывает правила переопределения для связи, описываемой элементом `AttributeRelationship`.|  
|[Элемент PartitionID &#40;ASSL&#41;](partitionid-element-assl.md)|Связывает элемент `Partition` с родительским элементом, привязкой или внешней привязкой.|  
|[Элемент Password &#40;ASSL&#41;](password-element-assl.md)|Содержит пароль учетной записи пользователя для элемента `ImpersonationInfo`.|  
|[Путь к элементу &#40;ASSL&#41;](path-element-assl.md)|Содержит путь, предоставленный экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], используемые отчета [ReportAction](../data-type/reportaction-data-type-assl.md) элемента.|  
|[Элемент PendingValue &#40;ASSL&#41;](pendingvalue-element-assl.md)|Содержит доступное только для чтения значение ожидания связанного элемента `ServerProperty`.|  
|[Элемент PermissionSet &#40;ASSL&#41;](permissionset-element-assl.md)|Определяет набор разрешений, связанных с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] сборки .NET Framework.|  
|[Элемент Persistence &#40;ASSL&#41;](persistence-element-assl.md)|Определяет фрагменты связанного источника данных являются динамическими и проверяются на обновления с частотой, указанной в [RefreshPolicy](refreshpolicy-element-assl.md) элемента.|  
|[Обработать элемент &#40;ASSL&#41;](process-element-assl.md)|Определяет, может ли пользователь проводить обработку владельца родительского элемента.|  
|[Элемент ProcessingMode &#40;ASSL&#41;](processingmode-element-assl.md)|Определяет, следует ли экземпляру производить индексирование и статистическую обработку во время работы или после нее.|  
|[Элемент ProcessingPriority &#40;ASSL&#41;](processingpriority-element-assl.md)|Определяет приоритет обработки для родительского объекта во время работы в фоновом режиме (например: отложенная статистическая обработка, индексирование или кластеризация).|  
|[Элемент ProcessingQuery &#40;ASSL&#41;](query-element-assl.md)|Содержит параметризованный текст запроса, который следует выполнить для уведомления о состоянии добавочной обработки.|  
|[Элемент ProductName &#40;ASSL&#41;](productname-element-assl.md)|Содержит доступное только для чтения название продукта экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], связанного с элементом `Server`.|  
|[Элемент запроса &#40;ASSL&#41;](query-element-assl.md)|Содержит текст запроса, который следует выполнить для создания уведомления.|  
|[Элемент QueryDefinition &#40;ASSL&#41;](querydefinition-element-assl.md)|Содержит непрозрачное выражение для запроса, связанного с `DataSource` элемент в [QueryBinding](../data-type/querybinding-data-type-assl.md) элемента.|  
|[Чтение элемента &#40;ASSL&#41;](read-element-assl.md)|Определяет, можно ли читать данные или метаданные для заданного [CubeDimensionPermission](../data-type/permission-data-type-assl.md) или [разрешение](../data-type/permission-data-type-assl.md) элемента.|  
|[Элемент ReadDefinition &#40;ASSL&#41;](readdefinition-element-assl.md)|Определяет, могут ли элементы читать определение базы данных или определение объектов в базе данных.|  
|[Элемент ReadSourceData &#40;ASSL&#41;](readsourcedata-element-assl.md)|Определяет правила формирования уникальных имен для иерархий, содержащихся в элементе `CubePermission`.|  
|[Элемент RefreshInterval &#40;ASSL&#41;](refreshinterval-element-assl.md)|Определяет интервал, с которым обновляются привязанные данные, связанные с родительским элементом.|  
|[Элемент RefreshPolicy &#40;ASSL&#41;](refreshpolicy-element-assl.md)|Определяет, как часто в динамической части измерения или группы мер (как указано в [сохраняемости](persistence-element-assl.md) элемент) проверяется на изменения.|  
|[Элемент RelationshipType &#40;ASSL&#41;](relationshiptype-element-assl.md)|Показывает, возможно ли изменение связей элементов для свойства `AttributeRelationship`.|  
|[Элемент RemoteDatasourceID &#40;ASSL&#41;](remotedatasourceid-element-assl.md)|Задает идентификатор источника данных OLAP, который указывает на экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], хранящий удаленную секцию.|  
|[Элемент ReportingFirstMonth &#40;ASSL&#41;](reportingfirstmonth-element-assl.md)|Определяет первый отчетный месяц для элемента `TimeBinding`.|  
|[Элемент ReportingFirstWeekOfMonth &#40;ASSL&#41;](reportingfirstweekofmonth-element-assl.md)|Определяет первую неделю отчетного месяца для элемента `TimeBinding`.|  
|[Элемент ReportingWeekToMonthPattern &#40;ASSL&#41;](reportingweektomonthpattern-element-assl.md)|Определяет шаблон соответствия отчетных недель и месяцев для элемента `TimeBinding`.|  
|[Элемент ReportServer &#40;ASSL&#41;](reportserver-element-assl.md)|Содержит имя экземпляра служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], который используется элементом `ReportAction`.|  
|[Элемент RequiresRestart &#40;ASSL&#41;](requiresrestart-element-assl.md)|Содержит значение только для чтения, связанное с элементом `ServerProperty`, которое определяет, требуется ли при изменении свойства сервера перезапускать экземпляр, чтобы изменения вступили в силу.|  
|[Элемент RoleID &#40;ASSL&#41;](roleid-element-assl.md)|Указывает роль, для которой определяются разрешения.|  
|[Корневой элемент &#40;ASSL&#41;](root-element-assl.md)|Содержит данные (набор строк) для источника данных.|  
|[Элемент RootMemberIf &#40;ASSL&#41;](rootmemberif-element-assl.md)|Определяет, как идентифицируются корневой элемент или элементы родительского атрибута.|  
|[Элемент schema &#40;ASSL&#41;](schema-element-assl.md)|Содержит схему представления источников данных.|  
|[Элемент ScriptCacheProcessingMode &#40;ASSL&#41;](scriptcacheprocessingmode-element-assl.md)|Указывает, должен ли сервер строить кэш скриптов во время или после обработки.|  
|[Элемент SilenceInterval &#40;ASSL&#41;](silenceinterval-element-assl.md)|Определяет минимальное количество времени, на которое экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] приостанавливается перед запуском процесса создания образа MOLAP.|  
|[Элемент SilenceOverrideInterval &#40;ASSL&#41;](silenceoverrideinterval-element-assl.md)|Определяет количество времени, которое должно пройти от получения начального уведомления до момента безусловного начала процесса создания образа MOLAP.|  
|[Элемент slice &#40;ASSL&#41;](slice-element-assl.md)|Содержит многомерное выражение, определяющее срез, содержащийся в секции.|  
|[Элемент SolveOrder &#40;ASSL&#41;](solveorder-element-assl.md)|Показывает порядок вычисления, в соответствии с которым элемент `CalculationProperty` применяется к вычисляемому элементу или к определению вычисляемой ячейки.|  
|[Элемент Source &#40;привязки&#41; &#40;ASSL&#41;](source-element-binding-assl.md)|Определяет источник данных, к которому привязан родительский элемент.|  
|[Элемент Source &#40;ComAssembly&#41; &#40;ASSL&#41;](source-element-comassembly-assl.md)|Содержит имя файла или программный идентификатор (ProgID) для COM-компонента.|  
|[Элемент Source &#40;мер&#41; &#40;ASSL&#41;](source-element-measure-assl.md)|Содержит сведения об источнике, содержащем значение элемента `Measure`.|  
|[Элемент SourceAttributeID &#40;ASSL&#41;](sourceattributeid-element-assl.md)|Содержит идентификатор исходного атрибута, на котором [уровень](../objects/level-element-assl.md) основан элемент.|  
|[Элемент SourceColumnID &#40;ASSL&#41;](sourcecolumnid-element-assl.md)|Содержит идентификатор столбца источника структуры интеллектуального анализа данных в предке элемента `MiningStructure`.|  
|[Состояние элемента &#40;ASSL&#41;](state-element-assl.md)|Содержит значение только для чтения, описывающее текущее состояние обработки родительского элемента.|  
|[Элемент Status &#40;ASSL&#41;](status-element-assl.md)|Содержит многомерное выражение, возвращающее признак состояния элемента `Kpi`.|  
|[Элемент StatusGraphic &#40;ASSL&#41;](statusgraphic-element-assl.md)|Содержит рекомендованное графическое представление состояния элемента `Kpi`.|  
|[Элемент StopTime &#40;ASSL&#41;](stoptime-element-assl.md)|Задает дату и время остановки элемента `Trace`.|  
|[Элемент StorageLocation &#40;ASSL&#41;](storagelocation-element-assl.md)|Содержит расположение места хранения в файловой системе для содержимого родительского элемента.|  
|[Элемент StorageMode &#40;ASSL&#41;](storagemode-element-assl.md)|Определяет режим хранения для родительского элемента.|  
|[Элемент TableID &#40;ASSL&#41;](tableid-element-assl.md)|Содержит идентификатор таблицы (из элемента `DataSourceView`), связанной с родительским элементом.|  
|[Целевой элемент &#40;ASSL&#41;](target-element-assl.md)|Определяет цель элемента `Action`.|  
|[Элемент TargetType &#40;ASSL&#41;](targettype-element-assl.md)|Определяет тип элемента, определенного в [целевой](target-element-assl.md) элемента.|  
|[Текстовый элемент &#40;ASSL&#41;](text-element-assl.md)|Содержит текст [команда](../objects/command-element-assl.md) элемента.|  
|[Элемент timeout &#40;ASSL&#41;](timeout-element-assl.md)|Задает время в секундах, по истечении которого для попытки извлечения данных сообщается о превышении времени ожидания.|  
|[Тренд элемент &#40;ASSL&#41;](trend-element-assl.md)|Содержит многомерное выражение, возвращающее признак тренда для элемента `Kpi`.|  
|[Элемент TrendGraphic &#40;ASSL&#41;](trendgraphic-element-assl.md)|Содержит рекомендованное графическое представление тренда элемента `Kpi`.|  
|[Элемент trimming &#40;ASSL&#41;](trimming-element-assl.md)|Определяет, как выполняется усечение пробелов в данных из источника данных.|  
|[Элемент type &#40;действия&#41; &#40;ASSL&#41;](type-element-action-assl.md)|Содержит тип элемента `Action`.|  
|[Элемент type &#40;привязки&#41; &#40;ASSL&#41;](type-element-binding-assl.md)|Содержит тип привязки атрибута.|  
|[Элемент type &#40;ClrAssemblyFile&#41; &#40;ASSL&#41;](type-element-clrassemblyfile-assl.md)|Задает тип файла одного из файлов, принадлежащих к сборке .NET Framework.|  
|[Элемент type &#40;измерения&#41; &#40;ASSL&#41;](type-element-dimension-assl.md)|Предоставляет данные о содержимом измерения.|  
|[Элемент type &#40;DimensionAttribute&#41; &#40;ASSL&#41;](type-element-dimensionattribute-assl.md)|Содержит тип атрибута.|  
|[Элемент type &#40;MeasureGroup&#41; &#40;ASSL&#41;](type-element-measuregroup-assl.md)|Указывает тип элемента `MeasureGroup`.|  
|[Элемент type &#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](type-element-measuregroupattribute-assl.md)|Содержит тип [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) элемента.|  
|[Элемент type &#40;MiningStructureColumn&#41; &#40;ASSL&#41;](type-element-miningstructurecolumn-assl.md)|Содержит тип [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) элемента.|  
|[Элемент type &#40;секции&#41; &#40;ASSL&#41;](type-element-partition-assl.md)|Содержит тип элемента `Partition`.|  
|[Элемент type &#40;PerspectiveCalculation&#41; &#40;ASSL&#41;](type-element-perspectivecalculation-assl.md)|Указывает тип [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) элемента.|  
|[Элемент UnknownMember &#40;ASSL&#41;](unknownmember-element-assl.md)|Показывает, видим ли неизвестный элемент.|  
|[Элемент UnknownMemberName &#40;ASSL&#41;](unknownmembername-element-assl.md)|Содержит заголовок (на языке по умолчанию для измерения) для неизвестного элемента измерения.|  
|[Элемент Usage &#40;DimensionAttribute&#41; &#40;ASSL&#41;](usage-element-dimensionattribute-assl.md)|Описывает, как используется атрибут.|  
|[Элемент Usage &#40;MiningModelColumn&#41; &#40;ASSL&#41;](usage-element-miningmodelcolumn-assl.md)|Описывает, как используется связанный столбец в родительском элементе `MiningStructure`.|  
|[Значение элемента &#40;ASSL&#41;](value-element-assl.md)|Содержит значение родительского элемента.|  
|[Элемент Version &#40;ASSL&#41;](version-element-assl.md)|Содержит доступный только для чтения номер версии экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], представляемого элементом `Server`.|  
|[Элемент Visibility &#40;ASSL&#41;](visibility-element-assl.md)|Определяет видимость элемента [заметки](../objects/annotation-element-assl.md) элемента.|  
|[Элемент Visible &#40;ASSL&#41;](visible-element-assl.md)|Определяет видимость родительского элемента.|  
|[Элемент VisualTotals &#40;ASSL&#41;](visualtotals-element-assl.md)|Содержит многомерное выражение, определяющее, отображаются ли визуальные итоги для элементов этого атрибута.|  
|[Элемент Write &#40;ASSL&#41;](write-element-assl.md)|Определяет, могут ли быть записаны метаданные для данного элемента `CubeDimensionPermission` или `Permission`.|  
|[Элемент WriteEnabled &#40;ASSL&#41;](writeenabled-element-assl.md)|Показывает, доступна ли обратная запись в измерение (зависит от прав доступа).|  
  
## <a name="see-also"></a>См. также  
 [Иерархия элементов XML для языка сценариев служб аналитики &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  