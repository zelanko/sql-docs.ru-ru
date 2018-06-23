---
title: Объекты (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASSL, objects
- objects [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
ms.assetid: 0f672b93-c317-47e5-b44d-ecea9b587c98
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 246126f6ec82a104b05687c088c0bf3d2a614da6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099419"
---
# <a name="objects-assl"></a>Объекты (ASSL)
  В данном разделе приведены сведения о синтаксисте и использовании каждого элемента, выступающего в роли объекта в схеме ASSL.  
  
 Несмотря на то, что в схеме языка ASSL содержатся только элементы XML, с точки зрения разработчика, элементы, описанные в этом разделе относятся к объекты, такие как `Database`, `Cube`, и `Dimension` объектов в иерархии объектов, содержащихся в экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Объекты в схеме ASSL никогда не бывают элементами конечного уровня и содержат дочерние элементы, соответствующие свойствам объектов.  
  
 В редких случаях конечный элемент в схеме, который выглядит как свойство, классифицируется как объект, поскольку тип элемента является типом объекта. Например, `Source` объекта `Dimension` имеет тип `DimensionBinding`.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Учетная запись элемент &#40;ASSL&#41;](account-element-assl.md)|Содержит сведения о типе счета в [базы данных](database-element-assl.md) элемента.|  
|[Элемент Action &#40;ASSL&#41;](action-element-assl.md)|Содержит сведения о действии, доступном в [куба](cube-element-assl.md) элемент или [перспективы](perspective-element-assl.md) элемента.|  
|[Элемент Aggregation &#40;ASSL&#41;](aggregation-element-assl.md)|Определяет один агрегат для [секции](partition-element-assl.md) элемента.|  
|[Элемент AggregationDesign &#40;ASSL&#41;](aggregationdesign-element-assl.md)|Определяет набор определений агрегатов, которые можно совместно использовать в разных секциях в базе данных.|  
|[Элемент AggregationInstance &#40;ASSL&#41;](aggregationinstance-element-assl.md)|Определяет экземпляр агрегата для секции.|  
|[Элемент AlgorithmParameter &#40;ASSL&#41;](algorithmparameter-element-assl.md)|Определяет параметр для алгоритма, используемого в [MiningModel](miningmodel-element-assl.md) элемента.|  
|[Элемент AllMemberTranslation &#40;ASSL&#41;](translation-element-assl.md)|Содержит перевод заголовка элемента «все» [иерархии](hierarchy-element-assl.md) элемента.|  
|[Элемент annotation &#40;ASSL&#41;](annotation-element-assl.md)|Содержит элементы, использующиеся для расширения схемы ASSL.|  
|[Элемент Assembly &#40;ASSL&#41;](assembly-element-assl.md)|Представляет [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку или библиотеку динамической компоновки COM (DLL), связанную с [сервера](server-element-assl.md) элемент или [базы данных](database-element-assl.md) элемента.|  
|[Атрибут элемента &#40;ASSL&#41;](attribute-element-assl.md)|Содержит описание атрибута.|  
|[Элемент AttributeAllMemberTranslation &#40;ASSL&#41;](attributeallmembertranslation-element-assl.md)|Содержит перевод заголовка элемента «все» [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) элемента.|  
|[Элемент AttributePermission &#40;ASSL&#41;](attributepermission-element-assl.md)|Определяет разрешения членов элемента [роли](role-element-assl.md) элемент имеет атрибуты отдельного измерения в [куба](cube-element-assl.md) элемента.|  
|[Элемент AttributeRelationship &#40;ASSL&#41;](attributerelationship-element-assl.md)|Предоставляет подробные сведения о связи между двумя атрибутами.|  
|[Блокировать элемент &#40;ASSL&#41;](block-element-assl.md)|Содержит все или часть двоичного содержимого [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) элемента.|  
|[Элемент CALCULATION &#40;ASSL&#41;](calculation-element-assl.md)|Связывает вычисление с [перспективы](perspective-element-assl.md) элемента.|  
|[Элемент CalculationProperty &#40;ASSL&#41;](calculationproperty-element-assl.md)|Содержит коллекцию свойств пользовательского интерфейса для вычисления, используемого в [MdxScript](mdxscript-element-assl.md) элемента.|  
|[Элемент CaptionColumn &#40;ASSL&#41;](column-element-assl.md)|Определяет столбец с заголовком атрибута.|  
|[Элемент CellPermission &#40;ASSL&#41;](cellpermission-element-assl.md)|Описывает разрешения, которые элементы элемента [роли](role-element-assl.md) имеют для отдельных ячеек в [куба](cube-element-assl.md) элемента.|  
|[Элемент COLUMN &#40;ASSL&#41;](column-element-assl.md)|Описывает столбец в коллекции столбцов, связанной с родительским элементом.|  
|[Команда элемент &#40;ASSL&#41;](command-element-assl.md)|Определяет команду, которую можно использовать в контексте родительского элемента коллекции «Commands».|  
|[Куб элемент &#40;ASSL&#41;](cube-element-assl.md)|Определяет обычный, виртуальный или связанный куб в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [базы данных](database-element-assl.md) элемента.|  
|[Элемент CubePermission &#40;ASSL&#41;](cubepermission-element-assl.md)|Определяет разрешения элементов конкретного [роли](role-element-assl.md) элемента в указанном [куба](cube-element-assl.md) элемента.|  
|[Элемент CustomRollupColumn &#40;ASSL&#41;](customrollupcolumn-element-assl.md)|Определяет подробные сведения столбца, содержащего формулу пользовательской свертки.|  
|[Элемент CustomRollupPropertiesColumn &#40;ASSL&#41;](customrolluppropertiescolumn-element-assl.md)|Определяет подробные сведения столбца, содержащего свойства формулы пользовательской свертки.|  
|[Элемент данных &#40;ASSL&#41;](data-element-assl.md)|Содержит (в коллекцию дочерних `Block` элементы) двоичное содержимое [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) элемента.|  
|[Элемент Database &#40;ASSL&#41;](database-element-assl.md)|Определяет базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент DatabasePermission &#40;ASSL&#41;](databasepermission-element-assl.md)|Определяет разрешения по умолчанию в [базы данных](database-element-assl.md) для конкретного элемента [роли](role-element-assl.md) элемента.|  
|[Элемент DataSource &#40;ASSL&#41;](datasource-element-assl.md)|Определяет источник данных в [базы данных](database-element-assl.md) элемента.|  
|[Элемент DataSourcePermission &#40;ASSL&#41;](datasourcepermission-element-assl.md)|Определяет разрешения по умолчанию в [DataSource](../data-type/datasource-data-type-assl.md) тип данных для конкретного [роли](role-element-assl.md) элемента.|  
|[Элемент DataSourceView &#40;ASSL&#41;](datasourceview-element-assl.md)|Определяет представление источника данных, используемое [базы данных](database-element-assl.md) элемента.|  
|[Элемент измерения &#40;ASSL&#41;](dimension-element-assl.md)|Определяет измерение.|  
|[Элемент DimensionPermission &#40;ASSL&#41;](dimensionpermission-element-assl.md)|Задает разрешения на определенное измерение базы данных или измерение куба, принадлежащие конкретному элементу [Role](role-element-assl.md) .|  
|[Элемент ErrorConfiguration &#40;ASSL&#41;](errorconfiguration-element-assl.md)|Задает параметры обработки ошибок, которые возникают при обработке родительского элемента.|  
|[Элемент Event &#40;ASSL&#41;](event-element-assl.md)|Определяет событие, фиксируемое как часть [трассировки](trace-element-assl.md) элемента.|  
|[Файл элемента &#40;ASSL&#41;](file-element-assl.md)|Определяет один из файлов, составляющих [ClrAssembly](../data-type/assembly-data-type-assl.md) элемента.|  
|[Элемент ForeignKeyColumn &#40;ASSL&#41;](keycolumn-element-assl.md)|Определяет соединение с родительской таблицей для реляционного источника данных.|  
|[Элемент Group &#40;ASSL&#41;](group-element-assl.md)|Определяет группу элементов, привязанных к атрибуту.|  
|[Элемент Hierarchy &#40;ASSL&#41;](hierarchy-element-assl.md)|Определяет иерархию в измерении.|  
|[Элемент IncrementalProcessingNotification &#40;ASSL&#41;](incrementalprocessingnotification-element-assl.md)|Содержит сведения о [ProactiveCaching](proactivecaching-element-assl.md) о запросе, следует выполнить для определения хода выполнения добавочной обработки.|  
|[Элемент KeyColumn &#40;ASSL&#41;](keycolumn-element-assl.md)|Содержит определение столбца, который является ключевым или входит в состав ключа для атрибута.|  
|[Элемент KPI &#40;ASSL&#41;](kpi-element-assl.md)|Определяет ключевой показатель эффективности (KPI) в пределах [куба](cube-element-assl.md) элемент или [перспективы](perspective-element-assl.md) элемента.|  
|[Уровень элемента &#40;ASSL&#41;](level-element-assl.md)|Определяет уровень в [иерархии](hierarchy-element-assl.md) элемента.|  
|[Элемент MdxScript &#40;ASSL&#41;](mdxscript-element-assl.md)|Содержит сведения о скрипте многомерных выражений (MDX), с которым связан [куба](cube-element-assl.md) элемента.|  
|[Элемент измерения &#40;ASSL&#41;](measure-element-assl.md)|Определяет меру.|  
|[Элемент MeasureGroup &#40;ASSL&#41;](measuregroup-element-assl.md)|Определяет набор мер на одном уровне гранулярности.|  
|[Элемент member &#40;ASSL&#41;](member-element-assl.md)|Содержит имя элемента [Group](group-element-assl.md) или [Role](role-element-assl.md) .|  
|[Элемент MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)|Определяет одну модель интеллектуального анализа данных.|  
|[Элемент MiningModelPermission &#40;ASSL&#41;](miningmodelpermission-element-assl.md)|Определяет разрешения членов [роли](role-element-assl.md) имеют для отдельных [MiningModel](miningmodel-element-assl.md) элемента.|  
|[Элемент MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)|Определяет структуру для набора моделей интеллектуального анализа данных.|  
|[Элемент MiningStructurePermission &#40;ASSL&#41;](miningstructurepermission-element-assl.md)|Определяет разрешения членов элемента [роли](role-element-assl.md) имеют для отдельных [MiningStructure](miningstructure-element-assl.md) элемента.|  
|[Элемент ModelingFlag &#40;ASSL&#41;](modelingflag-element-assl.md)|Содержит флаг моделирования для столбца в структуре или модели интеллектуального анализа данных.|  
|[Элемент NameColumn &#40;ASSL&#41;](namecolumn-element-assl.md)|Идентифицирует столбец, предоставляющий имя родительского элемента.|  
|[Элемент NamingTemplateTranslation &#40;ASSL&#41;](namingtemplatetranslation-element-assl.md)|Предоставляет локализованный перевод элемента `NamingTemplate` для родительского [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) тип данных.|  
|[Секции элемент &#40;ASSL&#41;](partition-element-assl.md)|Определяет секцию элемента [MeasureGroup](measuregroup-element-assl.md) элемента или привязку секции во вне строки [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)элемента.|  
|[Элемент perspective &#40;ASSL&#41;](perspective-element-assl.md)|Определяет подробные сведения для перспективы элемента [куба](cube-element-assl.md) элемента.|  
|[Элемент ProactiveCaching &#40;ASSL&#41;](proactivecaching-element-assl.md)|Определяет настройки упреждающего кэширования для родительского элемента.|  
|[Элемент QueryNotification &#40;ASSL&#41;](querynotification-element-assl.md)|Содержит сведения о [ProactiveCaching](proactivecaching-element-assl.md) о запросе, необходимо выполнить, чтобы определить, был ли изменен источник данных.|  
|[Элемент ReportFormatParameter &#40;ASSL&#41;](reportformatparameter-element-asl.md)|Содержит имя и значение параметра, указывающего, как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] форматирования отчета во время выполнения.|  
|[Элемент ReportParameter &#40;ASSL&#41;](reportparameter-element-assl.md)|Содержит имя и значение параметра, передаваемого отчету служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] во время выполнения.|  
|[Элемент Role &#40;ASSL&#41;](role-element-assl.md)|Содержит сведения о роли безопасности.|  
|[Элемент Server &#40;ASSL&#41;](server-element-assl.md)|Описывает экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент ServerProperty &#40;ASSL&#41;](serverproperty-element-assl.md)|Определяет свойство сервера, связанное с [сервера](server-element-assl.md) элемента.|  
|[Элемент SkippedLevelsColumn &#40;ASSL&#41;](skippedlevelscolumn-element-assl.md)|Предоставляет подробные сведения столбца, в котором хранится количество пропущенных (пустых) уровней между каждым элементом и его родительским элементом.|  
|[Элемент SourceMeasureGroup &#40;ASSL&#41;](sourcemeasuregroup-element-assl.md)|Определяет группу мер, которая выступает в роли источника данных для столбца структуры интеллектуального анализа данных.|  
|[Элемент TableNotification &#40;ASSL&#41;](tablenotification-element-assl.md)|Содержит сведения о [ProactiveCaching](proactivecaching-element-assl.md) о таблицы или представления в источнике данных, который был изменен.|  
|[Элемент Trace &#40;ASSL&#41;](trace-element-assl.md)|Определяет трассировку, к которой можно отправлять запросы.|  
|[Элемент Translation &#40;ASSL&#41;](translation-element-assl.md)|Предоставляет перевод для родительского элемента коллекции [Translations](../collections/translations-element-assl.md) .|  
|[Элемент UnaryOperatorColumn &#40;ASSL&#41;](unaryoperatorcolumn-element-assl.md)|Определяет подробные сведения столбца, содержащего унарный оператор.|  
|[Элемент UnknownMemberTranslation &#40;ASSL&#41;](unknownmembertranslation-element-assl.md)|Содержит перевод заголовка элемента [UnknownMember](../properties/unknownmember-element-assl.md) элемент для [измерения](dimension-element-assl.md) элемента.|  
|[Элемент ValueColumn &#40;ASSL&#41;](valuecolumn-element-assl.md)|Определяет столбец, предоставляющий значение родительского элемента.|  
  
## <a name="see-also"></a>См. также  
 [Иерархия элементов XML для языка сценариев служб аналитики &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  