---
title: Элемент ID (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71de55c773ce75ec75b38b774ad0a5e8ec35ed9b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170264"
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
|Родительские элементы|[Действие](../objects/action-element-assl.md), [статистической обработки](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [сборки](../objects/assembly-element-assl.md), [куба](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [базы данных](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [измерения ](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [иерархии](../objects/hierarchy-element-assl.md), [ключевого показателя эффективности](../objects/kpi-element-assl.md), [уровень](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Мер](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [ MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [секции](../objects/partition-element-assl.md), [разрешение](../data-type/permission-data-type-assl.md), [Перспективы](../objects/perspective-element-assl.md), [роли](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [трассировки](../objects/trace-element-assl.md)|  
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
 [Назовите элемент &#40;ASSL&#41;](name-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
