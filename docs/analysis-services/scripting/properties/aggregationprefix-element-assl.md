---
title: Элемент AggregationPrefix (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 224c954186bff2b8e08375bfccf43ad980209f87
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationprefix-element-assl"></a>Элемент AggregationPrefix (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
