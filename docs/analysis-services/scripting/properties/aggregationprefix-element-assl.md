---
title: "Элемент AggregationPrefix (ASSL) | Документы Microsoft"
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
- AggregationPrefix Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8ef1688e23bddf1136775474c93ae62a05bb97ab
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationprefix-element-assl"></a>Элемент AggregationPrefix (ASSL)
  Определяет общий префикс для имен агрегатов везде в связанном родительском элементе.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or Database, MeasureGroup, Partition -->  
   ...  
   <AggregationPrefix>...</AggregationPrefix>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../../../analysis-services/scripting/objects/cube-element-assl.md), [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Префиксы агрегатов применяются для формирования имен агрегатов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также формирования имен таблиц в реляционной базе данных для агрегатов, хранимых в секции реляционного OLAP (ROLAP).  
  
 Полностью уточненное имя агрегата состоит из следующих частей:  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Первые четыре части имени агрегата составляют префикс агрегата. Пользователь предоставляет первые четыре части.  
  
-   *DatabasePrefix* представляет значение элемента **AggregationPrefix** , связанного с элементом **Database** .  
  
-   *CubePrefix* представляет значение элемента **AggregationPrefix** , связанного с элементом **Cube** .  
  
-   *MeasureGroupPrefix* представляет значение элемента **AggregationPrefix** , связанного с элементом **MeasureGroup** .  
  
-   *PartitionPrefix* представляет значение элемента **AggregationPrefix** , связанного с элементом **Partition** .  
  
 Пятой частью имени, *AggregationID*, является идентификатор, определяемый системой, а пользователи не имеют контроля над этой частью имени.  
  
 Элементы, соответствующие родителям элемента **AggregationPrefix** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup>, и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

