---
title: "Элемент ID (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ID
helpviewer_keywords:
- ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e18410dd661afc19e42ba735f30728cad8f49bfc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="id-element-assl"></a>Элемент ID (ASSL)
  Содержит уникальный идентификатор родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
   <ID>...</ID>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (до 100 символов)|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md), [статистической обработки](../../../analysis-services/scripting/objects/aggregation-element-assl.md), [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [сборки](../../../analysis-services/scripting/objects/assembly-element-assl.md), [куба](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md), [измерения ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md), [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md), [уровень](../../../analysis-services/scripting/objects/level-element-assl.md), [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md), [Мер](../../../analysis-services/scripting/objects/measure-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [ MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md), [разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md), [Перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md), [роли](../../../analysis-services/scripting/objects/role-element-assl.md), [сервера](../../../analysis-services/scripting/objects/server-element-assl.md), [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Все главные объекты в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеет **идентификатор** элемент как свойство. Значение **идентификатор** элемент имеет следующие ограничения:  
  
-   Значение не может содержать начальные или конечные пробелы. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]неявно удалят начальные и конечные пробелы из значения **идентификатор** элемента.  
  
-   Значение не может содержать управляющие символы. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]неявно удалят управляющие символы из значения **идентификатор** элемента.  
  
-   Нельзя использовать следующие зарезервированные значения:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1-COM9 (COM1, COM2, COM3 и т. д.)  
  
    -   CON  
  
    -   LPT1-LPT9 (LPT1, LPT2, LPT3 и т. д.)  
  
    -   NUL  
  
    -   PRN  
  
 В следующей таблице перечислены дополнительные символы, которые не могут использоваться в значение **идентификатор** элемент, в зависимости от родительского элемента.  
  
|Родительский элемент|Символы|  
|--------------------|----------------|  
|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|Значение должно следовать правилам именования компьютеров [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. (IP-адреса недопустимы.)|  
|[Источник данных](../../../analysis-services/scripting/objects/datasource-element-assl.md)|:/\\*&#124;?"()[]{}<>|  
|[Уровень](../../../analysis-services/scripting/objects/level-element-assl.md), [атрибута элемента](../../../analysis-services/scripting/objects/attribute-element-assl.md)|.,;'`:/\\*&#124;?"&%$!+=[]{}<>|  
|Все остальные родительские элементы|.,;'`:/\\*&#124;?"&%$!+=()[]{}<>|  
  
## <a name="see-also"></a>См. также:  
 [Элемент Name &#40; ASSL &#41;](../../../analysis-services/scripting/properties/name-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

