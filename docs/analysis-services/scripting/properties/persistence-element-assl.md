---
title: Элемент Persistence (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c8911eafdcb6013cb97e85a9e1e428cabba50a46
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="persistence-element-assl"></a>Элемент Persistence (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Значение|Описание|  
|-----------|-----------------|  
|*NotPersisted*|Метаданные, элементы и данные источника являются динамическими.|  
|*Метаданные*|Метаданные источника являются статическими, а элементы и данные — динамическими.|  
|*все*|Метаданные, элементы и данные источника являются статическими.|  
  
 Перечисление, соответствующее разрешенным значениям для **сохраняемости** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PersistenceType>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
