---
title: Назовите элемент (ASSL) | Документация Майкрософт
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
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Name
helpviewer_keywords:
- Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7dde1de33d7ff2219bf2f73696c8a83236b46eb6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211594"
---
# <a name="name-element-assl"></a>Элемент Name (ASSL)
  Содержит имя родительского элемента.  
  
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
|Родительские элементы|[Действие](../objects/action-element-assl.md), [статистической обработки](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [заметки](../objects/annotation-element-assl.md), [ Сборка](../objects/assembly-element-assl.md), [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md), [куба](../objects/cube-element-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [Базы данных](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [измерения](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Группы](../objects/group-element-assl.md), [иерархии](../objects/hierarchy-element-assl.md), [ключевого показателя эффективности](../objects/kpi-element-assl.md), [уровень](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [ Мера](../objects/measure-element-assl.md), [MeasureGroup](../objects/measuregroup-element-assl.md), [MemberProperty](../objects/attributerelationship-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [ MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [секции](../objects/partition-element-assl.md), [разрешение](../data-type/permission-data-type-assl.md), [ Перспективы](../objects/perspective-element-assl.md), [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [ Роль](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md), [трассировки](../objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент, который используется для определения объекта (экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], иерархии, атрибута и т. д.) имеет `Name` элемент как свойство. На значение элемента `Name` накладываются следующие ограничения.  
  
-   Значение не может содержать начальные или конечные пробелы. Если в значении элемента `Name` имеются начальные или конечные пробелы, то они будут неявно удалены службой [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Значение не должно содержать управляющих символов. Использование управляющих символов в имени категорически не рекомендуется, иногда это может повлечь за собой ошибки проверки XML.  
  
     Для объектов, созданных с помощью метода `GetNewName` в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], объекты AMO проверяют, а затем удаляют в имени все управляющие символы, начальные или конечные пробелы. По этой причине использование `GetNewName` рекомендуется для задания имен объектов.  
  
     Однако, если задать свойство `Name` напрямую, такая проверка не выполняется, что может привести к ошибкам проверки XML. Зависит ли появление ошибки от того, какой управляющий символ встречается в имени.  
  
     Хотя управляющие символы вообще не следует использовать в имени объекта, службы Analysis Services не препятствуют этому в явной форме. Предыдущие выпуски служб Analysis Services иногда допускали управляющие символы в имени объекта. По этой причине [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] пропускает управляющие символы в имени объекта, чтобы избежать нарушения работы старых решений.  
  
-   Нельзя использовать следующие зарезервированные значения:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1-COM9 (COM1, COM2, COM3 и т. д.)  
  
    -   CON  
  
    -   LPT1-LPT9 (LPT1, LPT2, LPT3 и т. д.)  
  
    -   NUL  
  
    -   PRN  
  
 В следующей таблице перечислены дополнительные символы, которые нельзя использовать в значении элемента `Name`, в зависимости от родительского элемента.  
  
|Родительский элемент|Недопустимые символы|  
|--------------------|------------------------|  
|[Server](../objects/server-element-assl.md)|Имя должно соответствовать правилам именования для компьютеров [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. IP-адреса недопустимы.|  
|[Источник данных](../objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Уровень](../objects/level-element-assl.md), [атрибута элемента](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! [] +={}<>|  
|Все остальные родительские элементы|.,;' `:/\\*&#124;?" & % $! [] () +={}<>|  
  
## <a name="see-also"></a>См. также  
 [Элемент ID &#40;ASSL&#41;](id-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
