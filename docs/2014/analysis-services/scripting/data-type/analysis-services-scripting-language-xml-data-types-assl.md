---
title: Язык XML данных типы (ASSL) для создания скриптов служб Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Analysis Services Scripting Language XML Data Types
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
ms.assetid: 8e527916-932e-48ec-9010-f22cd4b721e2
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc773c4eda7b9f26b8ddafab5f6c80b068d32ec9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276640"
---
# <a name="analysis-services-scripting-language-xml-data-types-assl"></a>Типы данных XML в языке ASSL
  В этом разделе справки содержатся сведения о синтаксисе и об использовании каждого элемента, который выступает в качестве типа в схеме языка ASSL.  
  
 Хотя в схеме языка ASSL содержатся только элементы XML, но, с точки зрения разработчика, элементы, которые описываются в этом разделе, соответствуют типам (например `Binding` и `Permission`), которые используются для определения дочерних элементов и свойств других объектов.  
  
 Элементы типов, как и элементы объектов, никогда не являются элементами конечного уровня схемы ASSL. Они имеют дочерние элементы и элементы, соответствующие свойствам объектов.  
  
 Однако элемент типа никогда не отображается как элемент в скрипте, который определяет или описывает [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектов. Он может появиться в качестве типа других элементов-объектов, которые обычно создаются с атрибутом `type` из экземпляра XML-схемы, используя тип `xsi:type` или `xs:type`. Например, `<Assembly xsi:type="ClrAssembly">...</Assembly>`.  
  
 В некоторых случаях один тип является производным от другого типа. Например, тип `CubeBinding` является производным от родительского типа `Binding`.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Тип данных Action &#40;ASSL&#41;](action-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий действие в [куба](../objects/cube-element-assl.md) элемент или [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Тип данных AggregationAttribute &#40;ASSL&#41;](aggregationattribute-data-type-assl.md)|Определяет тип-примитив, представляющий взаимосвязь между [статистической обработки](../objects/aggregation-element-assl.md) элемента и атрибута.|  
|[Тип данных AggregationDesignAttribute &#40;ASSL&#41;](aggregationdesignattribute-data-type-assl.md)|Определяет тип-примитив, представляющий взаимосвязь между атрибутом и [AggregationDesignDimension](dimension-data-type-assl.md) элемент.|  
|[Тип данных AggregationDesignDimension &#40;ASSL&#41;](dimension-data-type-assl.md)|Определяет тип-примитив, представляющий связь между измерением куба и [AggregationDesign](../objects/aggregationdesign-element-assl.md) элемент.|  
|[Тип данных AggregationDimension &#40;ASSL&#41;](aggregationdimension-data-type-assl.md)|Определяет тип-примитив, представляющий связь между измерением и [статистической обработки](../objects/aggregation-element-assl.md) элемент.|  
|[Тип данных AggregationInstanceAttribute &#40;ASSL&#41;](aggregationinstanceattribute-data-type-assl.md)|Определяет примитивный тип данных, предоставляющий сведения об атрибуте, используемом экземпляром агрегата.|  
|[Тип данных AggregationInstanceCubeDimension &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Определяет примитивный тип данных, представляющий сведения об измерении куба, которое используется экземпляром агрегата.|  
|[Тип данных AggregationInstanceMeasure &#40;ASSL&#41;](aggregationinstancemeasure-data-type-assl.md)|Определяет примитивный тип данных, представляющий сведения о мере, которая используется экземпляром агрегата.|  
|[Тип данных Assembly &#40;ASSL&#41;](assembly-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку или библиотеку динамической компоновки COM (DLL), связанную с [Server](../objects/server-element-assl.md) или [базы данных](../objects/database-element-assl.md) элемент.|  
|[Тип данных AttributeBinding &#40;ASSL&#41;](binding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку для [атрибут](../objects/attribute-element-assl.md) элемента.|  
|[Тип данных AttributeTranslation &#40;ASSL&#41;](translation-data-type-assl.md)|Определяет производный тип данных, представляющий перевод, который связан с [атрибут](../objects/attribute-element-assl.md) элемент|  
|[Тип данных Binding &#40;ASSL&#41;](binding-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий связь зависимости между двумя объектами, в которых данные или метаданные одного объекта зависят от данных или метаданных привязанного объекта.|  
|[Тип данных ClrAssembly &#40;ASSL&#41;](clrassembly-data-type-assl.md)|Определяет производный тип данных, представляющий [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку, связанную с [базы данных](../objects/database-element-assl.md) или [Server](../objects/server-element-assl.md) элемент|  
|[Тип данных ClrAssemblyFile &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)|Определяет тип-примитив, представляющий один из файлов, составляющих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборки ([ClrAssembly](clrassembly-data-type-assl.md) элемент).|  
|[Тип данных ColumnBinding &#40;ASSL&#41;](columnbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку столбца в представлении источника данных для [DataItem](dataitem-data-type-assl.md) элемент.|  
|[Тип данных ComAssembly &#40;ASSL&#41;](comassembly-data-type-assl.md)|Определяет производный тип данных, представляющий библиотеку COM, связанную с [Server](../objects/server-element-assl.md) или [базы данных](../objects/database-element-assl.md) элемент.|  
|[Тип данных CubeAttribute &#40;ASSL&#41;](cubeattribute-data-type-assl.md)|Определяет тип-примитив, представляющий атрибут, связанный с [куба](../objects/cube-element-assl.md) элемент.|  
|[Тип данных CubeAttributeBinding &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Определяет производный тип данных, представляющий привязку атрибута в измерении куба к действию или к столбцу структуры интеллектуального анализа данных.|  
|[Тип данных CubeBinding &#40;вне строки&#41; &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Определяет тип-примитив, представляющий связь между [куба](../objects/cube-element-assl.md) элемент и [DataSource](../objects/datasource-element-assl.md) элемент.|  
|[Тип данных CubeDimension &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Определяет примитивный тип данных, представляющий связь между измерением и кубом.|  
|[Тип данных CubeDimensionBinding &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку [измерения](../objects/dimension-element-assl.md), [мер](../objects/measure-element-assl.md), или [MiningModel](../objects/miningmodel-element-assl.md) элемент на измерение куба.|  
|[Тип данных CubeDimensionPermission &#40;ASSL&#41;](permission-data-type-assl.md)|Определяет примитивный тип данных, представляющий разрешения на конкретное измерение в кубе для отдельной роли.|  
|[Тип данных CubeHierarchy &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Определяет тип-примитив, представляющий сведения об [иерархии](../objects/hierarchy-element-assl.md) элемент в [куба](../objects/cube-element-assl.md) элемент.|  
|[Тип данных DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)|Определяет тип-примитив, представляющий коллекцию блоков данных, используемых для хранения двоичного содержимого [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) элемент.|  
|[Тип данных DataItem &#40;ASSL&#41;](dataitem-data-type-assl.md)|Определяет примитивный тип данных, представляющий характеристики элемента данных, связанные с данными, например столбца или атрибута.|  
|[Тип данных DataMiningMeasureGroupDimension &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Определяет производный тип данных, представляющий связь между группой мер и измерением интеллектуального анализа данных.|  
|[Тип данных DataSource &#40;ASSL&#41;](datasource-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий источник данных в [базы данных](../objects/database-element-assl.md) элемент.|  
|[Тип данных DataSourceViewBinding &#40;ASSL&#41;](datasourceviewbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку представления источников данных к родительскому элементу.|  
|[Тип данных DegenerateMeasureGroupDimension &#40;ASSL&#41;](degeneratemeasuregroupdimension-data-type-assl.md)|Определяет производный тип данных, представляющий связь между вырожденным измерением (то есть измерением фактов) и группой мер.|  
|[Тип данных измерения &#40;ASSL&#41;](dimension-data-type-assl.md)|Определяет примитивный тип данных, представляющий измерение базы данных.|  
|[Тип данных DimensionAttribute &#40;ASSL&#41;](dimensionattribute-data-type-assl.md)|Определяет примитивный тип данных, представляющий атрибут в измерении.|  
|[Тип данных DimensionBinding &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку между источником данных и [измерения](../objects/dimension-element-assl.md) элемент.|  
|[Тип данных DimensionPermission &#40;ASSL&#41;](permission-data-type-assl.md)|Определяет производный тип данных, представляющий разрешения, назначенные измерению базы данных.|  
|[Тип данных DrillThroughAction &#40;ASSL&#41;](drillthroughaction-data-type-assl.md)|Определяет производный тип данных, представляющий действие детализации.|  
|[Тип данных DSVTableBinding &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку между таблицей и [DataSourceView](../objects/datasourceview-element-assl.md) элемент.|  
|[Тип данных EventColumn &#40;ASSL&#41;](eventcolumn-data-type-assl.md)|Определяет тип-примитив, представляющий столбец с данными, которые захватываются для [событий](../objects/event-element-assl.md) элемент как часть [трассировки](../objects/trace-element-assl.md) элемент.|  
|[Тип данных Hierarchy &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Определяет примитивный тип данных, представляющий иерархию в измерении.|  
|[Тип данных ImpersonationInfo &#40;ASSL&#41;](impersonationinfo-data-type-assl.md)|Определяет примитивный тип данных, представляющий сведения, которые используются для олицетворения пользователя.|  
|[Тип данных IncrementalProcessingNotification &#40;ASSL&#41;](incrementalprocessingnotification-data-type-assl.md)|Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) о запросе, необходимо выполнить, чтобы узнать ход выполнения добавочной обработки.|  
|[Тип данных InheritedBinding &#40;ASSL&#41;](inheritedbinding-data-type-assl.md)|Определяет производный тип данных, указывающий, что [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) наследует свои привязки от атрибута.|  
|[Тип данных ManyToManyMeasureGroupDimension &#40;ASSL&#41;](manytomanymeasuregroupdimension-data-type-assl.md)|Определяет производный тип данных, представляющий связь между измерением «многие ко многим» и группой мер.|  
|[Тип данных MeasureBinding &#40;ASSL&#41;](measurebinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку меры к родительскому элементу.|  
|[Тип данных MeasureGroupAttribute &#40;ASSL&#41;](measuregroupattribute-data-type-assl.md)|Определяет примитивный тип данных, представляющий связь между атрибутом и группой мер.|  
|[Тип данных MeasureGroupBinding &#40;ASSL&#41;](measuregroupbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку к [MeasureGroup](../objects/group-element-assl.md) элемент.|  
|[Тип данных MeasureGroupBinding &#40;вне строки&#41; &#40;ASSL&#41;](measuregroupbinding-data-type-out-of-line-assl.md)|Определяет примитивный тип данных, который представляет привязку к группе мер.|  
|[Тип данных MeasureGroupDimension &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий связь между измерением и группой мер.|  
|[Тип данных MeasureGroupDimensionBinding &#40;ASSL&#41;](measuregroupdimensionbinding-data-type-assl.md)|Определяет производный тип данных, представляющий связь между измерением и группой мер.|  
|[Тип данных MeasureGroupHierarchy &#40;ASSL&#41;](measuregrouphierarchy-data-type-assl.md)|Определяет примитивный тип данных, представляющий сведения об иерархии в группе мер.|  
|[Тип данных MiningModelColumn &#40;ASSL&#41;](miningmodelcolumn-data-type-assl.md)|Определяет тип-примитив, представляющий сведения о столбце в [MiningModel](../objects/miningmodel-element-assl.md) элемент.|  
|[Тип данных MiningModelingFlag &#40;ASSL&#41;](miningmodelingflag-data-type-assl.md)|Определяет тип-примитив, представляющий доступные флаги моделирования для [ModelingFlag](../objects/modelingflag-element-assl.md) элемент.|  
|[Тип данных MiningStructureColumn &#40;ASSL&#41;](miningstructurecolumn-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий сведения о столбце в [MiningStructure](../objects/miningstructure-element-assl.md) элемент.|  
|[Тип данных OlapDataSource &#40;ASSL&#41;](olapdatasource-data-type-assl.md)|Определяет производный тип данных, представляющий многомерный [DataSource](../objects/datasource-element-assl.md) элемент.|  
|[Тип данных PartitionBinding &#40;ASSL&#41;](partitionbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку к [секции](../objects/partition-element-assl.md) элемент.|  
|[Тип данных Permission &#40;ASSL&#41;](permission-data-type-assl.md)|Определяет абстрактный примитивный тип данных, представляющий сведения об отдельном разрешении.|  
|[Тип данных PerspectiveAction &#40;ASSL&#41;](perspectiveaction-data-type-assl.md)|Определяет тип-примитив, представляющий сведения о действии в [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Тип данных PerspectiveAttribute &#40;ASSL&#41;](perspectiveattribute-data-type-assl.md)|Определяет тип-примитив, представляющий сведения об атрибуте в [PerspectiveDimension](perspectivedimension-data-type-assl.md) элемент.|  
|[Тип данных PerspectiveCalculation &#40;ASSL&#41;](perspectivecalculation-data-type-assl.md)|Определяет тип-примитив, представляющий связь между вычислением и [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Тип данных PerspectiveDimension &#40;ASSL&#41;](perspectivedimension-data-type-assl.md)|Определяет примитивный тип данных, представляющий сведения об измерении в перспективе.|  
|[Тип данных PerspectiveHierarchy &#40;ASSL&#41;](perspectivehierarchy-data-type-assl.md)|Определяет тип-примитив, представляющий сведения об иерархии в [PerspectiveDimension](perspectivedimension-data-type-assl.md) элемент.|  
|[Тип данных PerspectiveKpi &#40;ASSL&#41;](perspectivekpi-data-type-assl.md)|Определяет тип-примитив, представляющий сведения о ключевой показатель эффективности (KPI) в [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Тип данных PerspectiveMeasure &#40;ASSL&#41;](perspectivemeasure-data-type-assl.md)|Определяет тип-примитив, представляющий сведения о мере в [PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md) элемент.|  
|[Тип данных PerspectiveMeasureGroup &#40;ASSL&#41;](perspectivemeasuregroup-data-type-assl.md)|Определяет тип-примитив, представляющий сведения о группе мер в [перспективы](../objects/perspective-element-assl.md) элемент.|  
|[Тип данных ProactiveCachingBinding &#40;ASSL&#41;](proactivecachingbinding-data-type-assl.md)|Определяет абстрактный производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) сведения об изменениях в источнике данных, которые требуют перестройки кэша, или о состоянии процесса перестройки.|  
|[Тип данных ProactiveCachingIncrementalProcessingBinding &#40;ASSL&#41;](proactivecachingincrementalprocessingbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку к [ProactiveCaching](../objects/proactivecaching-element-assl.md) сведений о состоянии процесса перестройки кэша.|  
|[Тип данных ProactiveCachingInheritedBinding &#40;ASSL&#41;](proactivecachinginheritedbinding-data-type-assl.md)|Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) об изменениях источника данных в таблицах и представлениях, определяемых через существующие привязки данных, которые требуют перестройки кэша.|  
|[Тип данных ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](proactivecachingobjectnotificationbinding-data-type-assl.md)|Определяет абстрактный производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) об изменениях источника данных, либо в указанных таблицах и представлениях, либо в таблицах и представлениях, определяемых через существующие привязки данных требующих перестройки кэша.|  
|[Тип данных ProactiveCachingQueryBinding &#40;ASSL&#41;](querybinding-data-type-assl.md)|Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) об изменениях источника данных в таблицах и представлениях, определяемых через исполнение указанных запросов, которые требуют перестройки кэша.|  
|[Тип данных ProactiveCachingTablesBinding &#40;ASSL&#41;](proactivecachingtablesbinding-data-type-assl.md)|Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) об изменениях источника данных в указанных таблицах и представлениях, требующих перестройки кэша.|  
|[Тип данных PushedDataSource &#40;ASSL&#41;](pusheddatasource-data-type-assl.md)|Определяет тип-примитив, представляющий источник данных (таких как [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] пакета) для «отправки» данных в [куба](../objects/cube-element-assl.md) элемент.|  
|[Тип данных QueryBinding &#40;ASSL&#41;](querybinding-data-type-assl.md)|Определяет производный тип данных, представляющий взаимосвязь [DataSource](../objects/datasource-element-assl.md) элемент с [QueryDefinition](../properties/querydefinition-element-assl.md) элемент.|  
|[Тип данных ReferenceMeasureGroupDimension &#40;ASSL&#41;](referencemeasuregroupdimension-data-type-assl.md)|Определяет производный тип данных, представляющий измерение, которое косвенно связано с таблицей фактов через промежуточное измерение (например группа мер Sales может ссылаться на измерение Geography, которое связывается через измерение Customer).|  
|[Тип данных RegularMeasureGroupDimension &#40;ASSL&#41;](regularmeasuregroupdimension-data-type-assl.md)|Определяет производный тип данных, представляющий обычную связь между измерением и группой мер.|  
|[Тип данных RelationalDataSource &#40;ASSL&#41;](relationaldatasource-data-type-assl.md)|Определяет производный тип данных, представляющий [DataSource](../objects/datasource-element-assl.md) основанный на реляционном источнике данных.|  
|[Тип данных ReportAction &#40;ASSL&#41;](reportaction-data-type-assl.md)|Определяет производный тип данных, который представляет действие, формирующее отчет служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Тип данных RowBinding &#40;ASSL&#41;](rowbinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку к строкам таблицы в [DataSourceView](../objects/datasourceview-element-assl.md) элемент.|  
|[Тип данных ScalarMiningStructureColumn &#40;ASSL&#41;](scalarminingstructurecolumn-data-type-assl.md)|Определяет производный тип данных, представляющий [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) элемент, содержащий скалярные значения, в отличие от вложенных таблиц, связанных с [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md) элемент содержащий вложенные таблицы.|  
|[Тип данных StandardAction &#40;ASSL&#41;](standardaction-data-type-assl.md)|Определяет производный тип данных, представляющий любой [действие](../objects/action-element-assl.md) элементом, кроме [DrillThroughAction](drillthroughaction-data-type-assl.md) элемент или [ReportAction](reportaction-data-type-assl.md) элемент.|  
|[Тип данных TableBinding &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку к таблице.|  
|[Тип данных TableMiningStructureColumn &#40;ASSL&#41;](tableminingstructurecolumn-data-type-assl.md)|Определяет производный тип данных, представляющий [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) элемент, который содержит вложенные таблицы, в отличие от скалярных значений, связанных с [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) элемент содержащий скалярные значения.|  
|[Тип данных TabularBinding &#40;ASSL&#41;](tabularbinding-data-type-assl.md)|Определяет абстрактный производный тип данных, представляющий привязку к табличному элементу, такому как таблица или измерение куба.|  
|[Тип данных TimeAttributeBinding &#40;ASSL&#41;](timebinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку-заполнитель для элементов данных, создаваемых в измерении времени сервера, например ключевых столбцов атрибута.|  
|[Тип данных TimeBinding &#40;ASSL&#41;](timebinding-data-type-assl.md)|Определяет производный тип данных, представляющий привязку к периодам времени.|  
|[Тип данных Translation &#40;ASSL&#41;](translation-data-type-assl.md)|Определяет примитивный тип данных, представляющий локализованный перевод.|  
|[Тип данных UserDefinedGroupBinding &#40;ASSL&#41;](userdefinedgroupbinding-data-type-assl.md)|Определяет производный тип данных, представляющий определенное пользователем группирование для атрибута.|  
  
## <a name="see-also"></a>См. также  
 [Иерархия элементов XML для языка сценариев служб аналитики &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
