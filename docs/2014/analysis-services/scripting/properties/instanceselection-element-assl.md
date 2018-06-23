---
title: Элемент InstanceSelection (ASSL) | Документы Microsoft
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
- InstanceSelection Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b36f0c3c5d29c88c499dea6e70ab4dd0cee1b42
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110035"
---
# <a name="instanceselection-element-assl"></a>Элемент InstanceSelection (ASSL)
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*None*|Не отображать список выбора. Разрешить пользователям вводить значения напрямую.|  
|*Раскрывающийся список*|Количество элементов достаточно мало для отображения в раскрывающемся списке.|  
|*Список*|Количество элементов слишком велико для отображения в раскрывающемся списке, но применение фильтров не требуется.|  
|*FilteredList*|Количество элементов достаточно велико, и для их отображения требуется использовать фильтр.|  
|*MandatoryFilter*|Количество элементов слишком велико для отображения даже после применения фильтра.|  
  
 Перечисление, соответствующее допустимым значениям элемента `InstanceSelection` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  