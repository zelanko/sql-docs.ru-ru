---
title: Объекты (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3171866b84dcaacf839d16560e6a228e318c3510
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="objects-assl"></a>Объекты (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В данном разделе приведены сведения о синтаксисте и использовании каждого элемента, выступающего в роли объекта в схеме ASSL.  
  
 Несмотря на то, что в схеме языка ASSL содержатся только элементы XML, с точки зрения разработчика, элементы, описанные в этом разделе относятся к объекты, такие как **базы данных**, **куба**, и  **Измерение** объектов в иерархии объектов, содержащихся в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Объекты в схеме ASSL никогда не бывают элементами конечного уровня и содержат дочерние элементы, соответствующие свойствам объектов.  
  
 В редких случаях конечный элемент в схеме, который выглядит как свойство, классифицируется как объект, поскольку тип элемента является типом объекта. Например **источника** из **измерения** объект имеет тип **DimensionBinding**.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Учетная запись элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/account-element-assl.md)|Содержит сведения о типе счета в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент Action &#40;ASSL&#41;](../../../analysis-services/scripting/objects/action-element-assl.md)|Содержит сведения о действии, доступном в элементе [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) или элементе [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md) .|  
|[Элемент Aggregation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)|Определяет один агрегат для [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) элемента.|  
|[Элемент AggregationDesign &#40;ASSL&#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)|Определяет набор определений агрегатов, которые можно совместно использовать в разных секциях в базе данных.|  
|[Элемент AggregationInstance &#40;ASSL&#41;](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|Определяет экземпляр агрегата для секции.|  
|[Элемент AlgorithmParameter &#40;ASSL&#41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|Определяет параметр для алгоритма, используемого в [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.|  
|[Элемент AllMemberTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/allmembertranslation-element-assl.md)|Содержит перевод заголовка элемента «все» [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.|  
|[Элемент annotation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/annotation-element-assl.md)|Содержит элементы, использующиеся для расширения схемы ASSL.|  
|[Элемент Assembly &#40;ASSL&#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)|Представляет [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку или библиотеку динамической компоновки COM (DLL), связанную с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемент или [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Атрибут элемента &#40;ASSL&#41;](../../../analysis-services/scripting/objects/attribute-element-assl.md)|Содержит описание атрибута.|  
|[Элемент AttributeAllMemberTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/attributeallmembertranslation-element-assl.md)|Содержит перевод заголовка элемента «все» [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) элемента.|  
|[Элемент AttributePermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)|Определяет разрешения членов элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемент имеет атрибуты отдельного измерения в [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент AttributeRelationship &#40;ASSL&#41;](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|Предоставляет подробные сведения о связи между двумя атрибутами.|  
|[Блокировать элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/block-element-assl.md)|Содержит все или часть двоичного содержимого [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) элемента.|  
|[Элемент CALCULATION &#40;ASSL&#41;](../../../analysis-services/scripting/objects/calculation-element-assl.md)|Связывает вычисление с [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элемента.|  
|[Элемент CalculationProperty &#40;ASSL&#41;](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|Содержит коллекцию свойств пользовательского интерфейса для вычисления, используемого в [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) элемента.|  
|[Элемент CaptionColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md)|Определяет столбец с заголовком атрибута.|  
|[Элемент CellPermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|Описывает разрешения, которые элементы элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) имеют для отдельных ячеек в [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент COLUMN &#40;ASSL&#41;](../../../analysis-services/scripting/objects/column-element-assl.md)|Описывает столбец в коллекции столбцов, связанной с родительским элементом.|  
|[Команда элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/command-element-assl.md)|Определяет команду, которую можно использовать в контексте родительского элемента коллекции «Commands».|  
|[Куб элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)|Определяет обычный, виртуальный или связанный куб в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент CubePermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)|Определяет разрешения элементов конкретного [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента в указанном [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент CustomRollupColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)|Определяет подробные сведения столбца, содержащего формулу пользовательской свертки.|  
|[Элемент CustomRollupPropertiesColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/customrolluppropertiescolumn-element-assl.md)|Определяет подробные сведения столбца, содержащего свойства формулы пользовательской свертки.|  
|[Элемент данных &#40;ASSL&#41;](../../../analysis-services/scripting/objects/data-element-assl.md)|Содержит (в коллекцию дочерних **блок** элементы) двоичное содержимое [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) элемента.|  
|[Элемент Database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)|Определяет базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент DatabasePermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|Определяет разрешения по умолчанию в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) для конкретного элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента.|  
|[Элемент DataSource &#40;ASSL&#41;](../../../analysis-services/scripting/objects/datasource-element-assl.md)|Определяет источник данных в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент DataSourcePermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/datasourcepermission-element-assl.md)|Определяет разрешения по умолчанию в [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) тип данных для конкретного [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента.|  
|[Элемент DataSourceView &#40;ASSL&#41;](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|Определяет представление источника данных, используемое [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.|  
|[Элемент измерения &#40;ASSL&#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)|Определяет измерение.|  
|[Элемент DimensionPermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|Задает разрешения на определенное измерение базы данных или измерение куба, принадлежащие конкретному элементу [Role](../../../analysis-services/scripting/objects/role-element-assl.md) .|  
|[Элемент ErrorConfiguration &#40;ASSL&#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|Задает параметры обработки ошибок, которые возникают при обработке родительского элемента.|  
|[Элемент Event &#40;ASSL&#41;](../../../analysis-services/scripting/objects/event-element-assl.md)|Определяет событие, фиксируемое как часть [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md) элемента.|  
|[Файл элемента &#40;ASSL&#41;](../../../analysis-services/scripting/objects/file-element-assl.md)|Определяет один из файлов, составляющих [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) элемента.|  
|[Элемент ForeignKeyColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md)|Определяет соединение с родительской таблицей для реляционного источника данных.|  
|[Элемент Group &#40;ASSL&#41;](../../../analysis-services/scripting/objects/group-element-assl.md)|Определяет группу элементов, привязанных к атрибуту.|  
|[Элемент Hierarchy &#40;ASSL&#41;](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|Определяет иерархию в измерении.|  
|[Элемент IncrementalProcessingNotification &#40;ASSL&#41;](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)|Содержит сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросе, следует выполнить для определения хода выполнения добавочной обработки.|  
|[Элемент KeyColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|Содержит определение столбца, который является ключевым или входит в состав ключа для атрибута.|  
|[Элемент KPI &#40;ASSL&#41;](../../../analysis-services/scripting/objects/kpi-element-assl.md)|Определяет ключевой показатель эффективности в элементе [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) или [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md) .|  
|[Уровень элемента &#40;ASSL&#41;](../../../analysis-services/scripting/objects/level-element-assl.md)|Определяет уровень в [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.|  
|[Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|Содержит сведения о скрипте многомерных выражений (MDX), с которым связан [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент измерения &#40;ASSL&#41;](../../../analysis-services/scripting/objects/measure-element-assl.md)|Определяет меру.|  
|[Элемент MeasureGroup &#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|Определяет набор мер на одном уровне гранулярности.|  
|[Элемент member &#40;ASSL&#41;](../../../analysis-services/scripting/objects/member-element-assl.md)|Содержит имя элемента [Group](../../../analysis-services/scripting/objects/group-element-assl.md) или [Role](../../../analysis-services/scripting/objects/role-element-assl.md) .|  
|[Элемент MiningModel &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|Определяет одну модель интеллектуального анализа данных.|  
|[Элемент MiningModelPermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)|Определяет разрешения членов [роли](../../../analysis-services/scripting/objects/role-element-assl.md) имеют для отдельных [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.|  
|[Элемент MiningStructure &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|Определяет структуру для набора моделей интеллектуального анализа данных.|  
|[Элемент MiningStructurePermission &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|Определяет разрешения членов элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) имеют для отдельных [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента.|  
|[Элемент ModelingFlag &#40;ASSL&#41;](../../../analysis-services/scripting/objects/modelingflag-element-assl.md)|Содержит флаг моделирования для столбца в структуре или модели интеллектуального анализа данных.|  
|[Элемент NameColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|Идентифицирует столбец, предоставляющий имя родительского элемента.|  
|[Элемент NamingTemplateTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/namingtemplatetranslation-element-assl.md)|Предоставляет локализованный перевод элемента **NamingTemplate** для родительского [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) тип данных.|  
|[Секции элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|Определяет секцию элемента [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) элемента или привязку секции во вне строки [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)элемента.|  
|[Элемент perspective &#40;ASSL&#41;](../../../analysis-services/scripting/objects/perspective-element-assl.md)|Определяет подробные сведения для перспективы элемента [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.|  
|[Элемент ProactiveCaching &#40;ASSL&#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|Определяет настройки упреждающего кэширования для родительского элемента.|  
|[Элемент QueryNotification &#40;ASSL&#41;](../../../analysis-services/scripting/objects/querynotification-element-assl.md)|Содержит сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросе, необходимо выполнить, чтобы определить, был ли изменен источник данных.|  
|[Элемент ReportFormatParameter &#40;ASSL&#41;](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)|Содержит имя и значение параметра, указывающего, как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] форматирования отчета во время выполнения.|  
|[Элемент ReportParameter &#40;ASSL&#41;](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|Содержит имя и значение параметра, передаваемого отчету служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] во время выполнения.|  
|[Элемент Role &#40;ASSL&#41;](../../../analysis-services/scripting/objects/role-element-assl.md)|Содержит сведения о роли безопасности.|  
|[Элемент Server &#40;ASSL&#41;](../../../analysis-services/scripting/objects/server-element-assl.md)|Описывает экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент ServerProperty &#40;ASSL&#41;](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|Определяет свойство сервера, связанное с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.|  
|[Элемент SkippedLevelsColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/skippedlevelscolumn-element-assl.md)|Предоставляет подробные сведения столбца, в котором хранится количество пропущенных (пустых) уровней между каждым элементом и его родительским элементом.|  
|[Элемент SourceMeasureGroup &#40;ASSL&#41;](../../../analysis-services/scripting/objects/sourcemeasuregroup-element-assl.md)|Определяет группу мер, которая выступает в роли источника данных для столбца структуры интеллектуального анализа данных.|  
|[Элемент TableNotification &#40;ASSL&#41;](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|Содержит сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о таблицы или представления в источнике данных, который был изменен.|  
|[Элемент Trace &#40;ASSL&#41;](../../../analysis-services/scripting/objects/trace-element-assl.md)|Определяет трассировку, к которой можно отправлять запросы.|  
|[Элемент Translation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)|Предоставляет перевод для родительского элемента коллекции [Translations](../../../analysis-services/scripting/collections/translations-element-assl.md) .|  
|[Элемент UnaryOperatorColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/unaryoperatorcolumn-element-assl.md)|Определяет подробные сведения столбца, содержащего унарный оператор.|  
|[Элемент UnknownMemberTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)|Содержит перевод заголовка элемента [UnknownMember](../../../analysis-services/scripting/properties/unknownmember-element-assl.md) элемент для [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md) элемента.|  
|[Элемент ValueColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/valuecolumn-element-assl.md)|Определяет столбец, предоставляющий значение родительского элемента.|  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services Scripting иерархия элементов XML языка & #40; ASSL & #41;](../../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
