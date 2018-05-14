---
title: Элемент InstanceSelection (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1f00127f58bb1f8c5a6792bec3ddcb8420f0d24b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="instanceselection-element-assl"></a>Элемент InstanceSelection (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет указания для клиентских приложений о том, как следует отображать список элементов на основе предполагаемого количества элементов в списке.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Description|  
|-----------|-----------------|  
|*None*|Не отображать список выбора. Разрешить пользователям вводить значения напрямую.|  
|*Раскрывающийся список*|Количество элементов достаточно мало для отображения в раскрывающемся списке.|  
|*Список*|Количество элементов слишком велико для отображения в раскрывающемся списке, но применение фильтров не требуется.|  
|*FilteredList*|Количество элементов достаточно велико, и для их отображения требуется использовать фильтр.|  
|*MandatoryFilter*|Количество элементов слишком велико для отображения даже после применения фильтра.|  
  
 Перечисление, соответствующее разрешенным значениям для **InstanceSelection** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
