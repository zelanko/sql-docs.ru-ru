---
title: "Коды типов, используемые для трассировки объектов служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e4119db1-4a41-4335-9b33-f1ea95564300
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7bd50f15603440953dc2f9c52ae669e5fcbd3108
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-object-type-codes-used-in-traces"></a>Коды типов объектов служб Analysis Services, используемые для трассировки
  На этой странице перечислены типы всех объектов (шестизначное число) модели данных служб Analysis Services. Эти коды отображаются в журналах трассировки и используются для определения типа объекта, связанного с определенной блокировкой. Например, время ожидания блокировки в базе данных будет указывать на тип объекта 100002, который является типом объекта базы данных.  
  
> [!NOTE]  
>  Ниже перечислено большее число кодов, чем в действительности будет отображаться в журнале трассировки. Ниже представлен полный список кодов типов для каждого объекта, но только те объекты, которые будут заблокированы, будут представлять код типа объекта в журнале трассировки.  
  
## <a name="object-type-reference"></a>Ссылка на тип объекта  
  
|Тип объекта|Имя объекта|  
|-----------------|-----------------|  
|100000|Server|  
|100001|Command|  
|100002|База данных|  
|100003|DataSource|  
|100004|DatabasePermission|  
|100005|Роль|  
|100006|Измерение|  
|100007|DimensionAttribute|  
|100008|Иерархия|  
|100009|Level|  
|100010|Cube|  
|100011|CubePermission|  
|100012|CubeDimension|  
|100013|CubeAttribute|  
|100014|CubeHierarchy|  
|100016|Группа мер|  
|100017|MeasureGroupDimension|  
|100018|MeasureGroupAttribute|  
|100020|Measure|  
|100021|Секция|  
|100025|AggregationDesign|  
|100026|AggregationDesignDimension|  
|100027|AggregationDesignAttribute|  
|100028|Агрегатная функция|  
|100029|AggregationDimension|  
|100030|AggregationAttribute|  
|100032|MiningStructure|  
|100033|MiningStructureColumn|  
|100037|MiningModel|  
|100038|MiningModelColumn|  
|100039|AlgorithmParameter|  
|100041|MiningModelPermission|  
|100042|DimensionPermission|  
|100043|MiningStructurePermission|  
|100044|Сборка|  
|100045|DatabaseRole|  
|100046|AttributePermission|  
|100047|CubeAttributePermission|  
|100048|CellPermission|  
|100049|CubeDimensionPermission|  
|100050|Trace|  
|100051|ServerAssembly|  
|100052|CubeAssembly|  
|100053|Command|  
|100054|Ключевой показатель эффективности|  
|100055|DataSourceView|  
|100056|Perspective|  
|100100|CommandCollection|  
|100101|DatabaseCollection|  
|100102|DataSourceCollection|  
|100103|DatabasePermission|  
|100104|RoleCollection|  
|100105|DimensionCollection|  
|100106|DimensionAttributeCollection|  
|100107|HierarchyCollection|  
|100108|LevelCollection|  
|100109|CubeCollection|  
|100110|CubePermissionCollection|  
|100111|CubeDimensionCollection|  
|100112|CubeAttributeCollection|  
|100113|CubeHierarchyCollection|  
|100115|MeasureGroupCollection|  
|100116|MeasureGroupDimensionCollection|  
|100117|MeasureGroupAttributeCollection|  
|100119|MeasureCollection|  
|100120|PartitionCollection|  
|100124|AggregationDesignCollection|  
|100125|AggregationDesignDimensionCollection|  
|100126|AggregationDesignAttributeCollection|  
|100127|AggregationCollection|  
|100128|AggregationDimensionCollection|  
|100129|AggregationAttributeCollection|  
|100131|MiningStructureCollection|  
|100132|MiningStructureColumnCollection|  
|100136|MiningModelCollection|  
|100137|MiningModelColumnCollection|  
|100138|AlgorithmParameterCollection|  
|100140|MiningModelPermissionCollection|  
|100141|DimensionPermissionCollection|  
|100142|MiningStructurePermissionCollection|  
|100143|AssemblyCollection|  
|100144|DatabaseRoleCollecction|  
|100145|AttributePermissionCollection|  
|100146|CubeAttributePermissionCollection|  
|100147|CellPermissionCollection|  
|100148|CubeDimensionPermissionCollection|  
|100149|TraceCollection|  
|100150|ServerAssemblyCollection|  
|100151|CubeAssemblyCollection|  
|100152|CommandCollection|  
|100153|KpiCollection|  
|100154|DataSourceViewCollection|  
|100155|PerspectiveCollection|  
  
  
