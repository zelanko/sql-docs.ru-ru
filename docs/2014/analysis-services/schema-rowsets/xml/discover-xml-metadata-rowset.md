---
title: Набор строк DISCOVER_XML_METADATA | Документы Microsoft
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
- DISCOVER_XML_METADATA
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4452408b36fe50300277d0d0f8e076357403539f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193461"
---
# <a name="discoverxmlmetadata-rowset"></a>Набор строк DISCOVER_XML_METADATA
  Возвращает XML-документ с описанием запрошенного объекта. Возвращаемый набор строк всегда состоит из одной строки и одного столбца.  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_XML_METATDATA` значения перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает `DISCOVER_XML_METATDATA` набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк `DISCOVER_XML_METADATA` содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`METADATA`|`DBTYPE_WSTR`||XML-документ, который описывает объект, требуемый в соответствии с ограничением.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Набор строк `DISCOVER_XML_METADATA` нельзя запрашивать с помощью синтаксиса команды SELECT. Однако набор строк `DISCOVER_XML_METADATA` можно запрашивать методом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_XML_METADATA` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`DatabaseID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DimensionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CubeID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MeasureGroupID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`PartitionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`PerspectiveID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DimensionPermissionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`RoleID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DatabasePermissionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MiningModelID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MiningModelPermissionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DataSourceID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MiningStructureID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`AggregationDesignID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`TraceID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MiningStructurePermissionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CubePermissionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`AssemblyID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MdxScriptID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DataSourceViewID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DataSourcePermissionID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`ObjectExpansion`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
 Ограничения, `ObjectExpansion`, доступных для каждого основного объекта служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В клиенте ограничения обычно используются для описания объектов OLAP, для которых должен быть возвращен код на языке DDL, а ограничение `ObjectExpansion` служит для определения степени развертывания в возвращаемом коде на языке DDL. Следующая таблица указывает, может ли значение перечисления для [Alter элемент &#40;XMLA&#41; ](../../xmla/xml-elements-commands/alter-element-xmla.md) команд.  
  
|Значение перечисления|Описание|  
|-----------------------|-----------------|  
|`ReferenceOnly`|Возвращает только имя/идентификатор/отметку времени/состояние, требуемое для запрашиваемых объектов, а также, рекурсивно, все основные объекты-потомки.|  
|`ObjectProperties`|Развертывает запрашиваемый объект без ссылок на содержащиеся объекты (включает развернутые более мелкие содержащиеся объекты).|  
|`ExpandObject`|Аналогичен параметру *ObjectProperties*, но также возвращает имя, идентификатор и отметку времени для вложенных основных объектов.|  
|`ExpandFull`|Полностью развертывает запрашиваемый объект рекурсивно до конца каждого содержащегося объекта.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  