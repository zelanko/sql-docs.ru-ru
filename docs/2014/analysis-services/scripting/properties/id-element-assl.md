---
title: Элемент ID (ASSL) | Документы Microsoft
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
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ID
helpviewer_keywords:
- ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0a1ad98b6b9609cf50d16816c8ae5328083a63ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193455"
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Action](../objects/action-element-assl.md), [Aggregation](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [Cube](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [Database](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Hierarchy](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [Level](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Measure](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [Partition](../objects/partition-element-assl.md), [Permission](../data-type/permission-data-type-assl.md), [Perspective](../objects/perspective-element-assl.md), [Role](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [Trace](../objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Все главные объекты в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеет `ID` элемент как свойство. Значение элемента `ID` имеет следующие ограничения.  
  
-   Значение не может содержать начальные или конечные пробелы. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] неявно удалят начальные и конечные пробелы из значения элемента `ID`.  
  
-   Значение не может содержать управляющие символы. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] неявно удалят управляющие символы из значения элемента `ID`.  
  
-   Нельзя использовать следующие зарезервированные значения:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1-COM9 (COM1, COM2, COM3 и т. д.)  
  
    -   CON  
  
    -   LPT1-LPT9 (LPT1, LPT2, LPT3 и т. д.)  
  
    -   NUL  
  
    -   PRN  
  
 В следующей таблице приводятся дополнительные символы, которые нельзя использовать в значениях элемента `ID`, в зависимости от родительского элемента.  
  
|Родительский элемент|Символы|  
|--------------------|----------------|  
|[Server](../objects/server-element-assl.md)|Значение должно следовать правилам именования компьютеров [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. (IP-адреса недопустимы.)|  
|[Источник данных](../objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Уровень](../objects/level-element-assl.md), [атрибута элемента](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! [] +={}<>|  
|Все остальные родительские элементы|.,;' `:/\\*&#124;?" & % $! [] () +={}<>|  
  
## <a name="see-also"></a>См. также  
 [Элемент Name &#40;ASSL&#41;](name-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  