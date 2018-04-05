---
title: Элемент InstanceSelection (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- InstanceSelection Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: db8918b9f172dc972eb59474c3bc1614d5251c02
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="instanceselection-element-assl"></a>Элемент InstanceSelection (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет указания для клиентских приложений о том, как список элементов следует отображать, на основе ожидаемого числа элементов в списке.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Description|  
|-----------|-----------------|  
|*None*|Не отображать список выбора. Разрешить пользователям вводить значения напрямую.|  
|*Раскрывающийся список*|Количество элементов достаточно мало для отображения в раскрывающемся списке.|  
|*Список*|Количество элементов слишком велико для отображения в раскрывающемся списке, но применение фильтров не требуется.|  
|*FilteredList*|Количество элементов достаточно велико, и для их отображения требуется использовать фильтр.|  
|*MandatoryFilter*|Количество элементов слишком велико для отображения даже после применения фильтра.|  
  
 Перечисление, соответствующее разрешенным значениям для **InstanceSelection** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.InstanceSelection>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
