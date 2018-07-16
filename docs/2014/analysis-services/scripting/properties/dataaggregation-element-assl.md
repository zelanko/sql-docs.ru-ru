---
title: Элемент DataAggregation (ASSL) | Документация Майкрософт
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
- DataAggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataAggregation element
ms.assetid: baf6d2c9-54f6-4a6d-95f7-e1e758be458d
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eca6c0e89bcc120334e179ad59c1dfce657ab057
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289590"
---
# <a name="dataaggregation-element-assl"></a>Элемент DataAggregation (ASSL)
  Определяет, является ли экземпляр выполнить статистическое вычисление материализованных или кэшированных данных для [MeasureGroup](../objects/group-element-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup>  
   ...  
   <DataAggregation>...</DataAggregation>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*DataAndCacheAggregatable*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Группа мер](../objects/group-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*None*|Для этой группы мер статистическая обработка не выполняется.|  
|*DataAggregatable*|Для этой группы мер статистическое вычисление может выполняться для материализованных данных.|  
|*CacheAggregatable*|Для этой группы мер статистическое вычисление может выполняться для кэшированных данных.|  
|*DataAndCacheAggregatable*|Для этой группы мер статистическое вычисление может выполняться как для материализованных данных, так и для кэшированных.|  
  
 Элемент, соответствующий родителю параметра `DataAggregation` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Элемент куба &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Элемент измерения &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
