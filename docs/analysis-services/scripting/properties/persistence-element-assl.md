---
title: "Элемент Persistence (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Persistence Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Persistence
helpviewer_keywords:
- Persistence element
ms.assetid: dafe3df2-4795-48ea-bebe-33c1a3bf18b6
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fd24f62070693d74949bd9ff328c87f66567929f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="persistence-element-assl"></a>Элемент Persistence (ASSL)
  Определяет фрагменты связанного источника данных являются динамическими и проверяются на обновления с частотой, указанной в [RefreshPolicy](../../../analysis-services/scripting/properties/refreshpolicy-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Persistence>...</Persistence>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*NotPersisted*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*NotPersisted*|Метаданные, элементы и данные источника являются динамическими.|  
|*Метаданные*|Метаданные источника являются статическими, а элементы и данные — динамическими.|  
|*все*|Метаданные, элементы и данные источника являются статическими.|  
  
 Перечисление, соответствующее разрешенным значениям для **сохраняемости** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PersistenceType>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
