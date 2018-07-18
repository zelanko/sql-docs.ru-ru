---
title: Элемент AggregationPrefix (ASSL) | Документация Майкрософт
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
- AggregationPrefix Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7f7fe7ad16c8949116edb13c7d2c9b5144443dd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293284"
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../objects/cube-element-assl.md), [базы данных](../objects/database-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [секции](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Префиксы агрегатов применяются для формирования имен агрегатов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также формирования имен таблиц в реляционной базе данных для агрегатов, хранимых в секции реляционного OLAP (ROLAP).  
  
 Полностью уточненное имя агрегата состоит из следующих частей:  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Первые четыре части имени агрегата составляют префикс агрегата. Пользователь предоставляет первые четыре части.  
  
-   *DatabasePrefix* представляет значение `AggregationPrefix` элемент, связанный с `Database` элемент.  
  
-   *CubePrefix* представляет значение `AggregationPrefix` элемент, связанный с `Cube` элемент.  
  
-   *MeasureGroupPrefix* представляет значение `AggregationPrefix` элемент, связанный с `MeasureGroup` элемент.  
  
-   *PartitionPrefix* представляет значение `AggregationPrefix` элемент, связанный с `Partition` элемент.  
  
 Пятой частью имени, *AggregationID*, является идентификатор, определяемый системой, а пользователи не имеют контроля над этой частью имени.  
  
 Элементы, соответствующие родителям элемента `AggregationPrefix` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup> и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
