---
title: "Назовите элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Name Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Name
helpviewer_keywords: Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 80a083e924e6265689f9852bae46b0c0c184c765
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="name-element-assl"></a>Элемент Name (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит имя родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Name>...</Name>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (до 100 символов)|  
|Значение по умолчанию|Возможны разные варианты|  
|Количество элементов|1-1: обязательный элемент, который встречается только один раз|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md), [статистической обработки](../../../analysis-services/scripting/objects/aggregation-element-assl.md), [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md), [заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md), [ Сборка](../../../analysis-services/scripting/objects/assembly-element-assl.md), [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md), [куба](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md), [Базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md), [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [Группы](../../../analysis-services/scripting/objects/group-element-assl.md), [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md), [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md), [уровень](../../../analysis-services/scripting/objects/level-element-assl.md), [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md), [ Меры](../../../analysis-services/scripting/objects/measure-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MemberProperty](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md), [ MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md), [разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md), [ Перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md), [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md), [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md), [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md), [ Роль](../../../analysis-services/scripting/objects/role-element-assl.md), [сервера](../../../analysis-services/scripting/objects/server-element-assl.md), [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md), [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Каждый элемент, который используется для определения объекта (экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], иерархии, атрибута и т. д) имеет **имя** элемент как свойство. Значение **имя** элемент имеет следующие ограничения:  
  
-   Значение не может содержать начальные или конечные пробелы. Если начальные или конечные пробелы будут включены в значение **имя** элемента, эти пробелы будут неявно удалены службой [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Значение не должно содержать управляющих символов. Использование управляющих символов в имени категорически не рекомендуется, иногда это может повлечь за собой ошибки проверки XML.  
  
     Для объектов, созданных с помощью **GetNewName** метод [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], объекты AMO, проверяет и впоследствии удаляет все управляющие символы, начальные или конечные пробелы в имени. Для этой причине использование **GetNewName** является рекомендуемым методом для задания имен объектов.  
  
     Тем не менее если задать **имя** свойство напрямую, такая проверка не выполняются проверки, что может привести к ошибкам проверки XML. Зависит ли появление ошибки от того, какой управляющий символ встречается в имени.  
  
     Хотя управляющие символы вообще не следует использовать в имени объекта, службы Analysis Services не препятствуют этому в явной форме. Предыдущие выпуски служб Analysis Services иногда допускали управляющие символы в имени объекта. Для этого причине, SQL Server 2016 Analysis Services и более поздней версии пропускает управляющие символы в имени объекта, чтобы избежать нарушения работы старых решений.  
  
-   Нельзя использовать следующие зарезервированные значения:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1-COM9 (COM1, COM2, COM3 и т. д.)  
  
    -   CON  
  
    -   LPT1-LPT9 (LPT1, LPT2, LPT3 и т. д.)  
  
    -   NUL  
  
    -   PRN  
  
 В следующей таблице перечислены дополнительные символы, которые не могут использоваться в значение **имя** элемента, в зависимости от родительского элемента.  
  
|Родительский элемент|Недопустимые символы|  
|--------------------|------------------------|  
|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|Имя должно соответствовать правилам именования для компьютеров [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. IP-адреса недопустимы.|  
|[Источник данных](../../../analysis-services/scripting/objects/datasource-element-assl.md)|:/\\*&#124;?"()[]{}<>|  
|[Уровень](../../../analysis-services/scripting/objects/level-element-assl.md), [атрибута элемента](../../../analysis-services/scripting/objects/attribute-element-assl.md)|.,;'`:/\\*&#124;?"&%$!+=[]{}<>|  
|Все остальные родительские элементы|.,;'`:/\\*&#124;?"&%$!+=()[]{}<>|  
  
## <a name="see-also"></a>См. также:  
 [Элемент ID &#40; ASSL &#41;](../../../analysis-services/scripting/properties/id-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
