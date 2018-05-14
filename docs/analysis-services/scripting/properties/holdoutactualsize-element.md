---
title: Элемент HoldoutActualSize | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9d73c9ba1e3028c3b5622bb27422fdb8774df518
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="holdoutactualsize-element"></a>Элемент HoldoutActualSize
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Отображает фактический размер, после обработки контрольной секции, содержащей проверочный набор элемента [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента. Остающиеся варианты в наборе данных используются для обучения. Это свойство предназначено только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutActualSize>...</ddl100_100:HoldoutActualSize>  
   ...  
</MiningStructure  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленное значение только для чтения.|  
|Значение по умолчанию|Неприменимо|  
|Количество элементов|0—1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение для **HoldoutActualSize** зависит от источника данных и значения для [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md), [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md), и [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md). Поэтому значение **HoldoutActualSize** недоступно до после [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] выполняет обработку структуры интеллектуального анализа данных.  
  
 Элемент, соответствующий родителю параметра **HoldoutActualSize** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] инструкций языка сценариев (ASSL), которые содержат один из параметров контрольных **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, или **HoldoutActualSize**, не может использоваться в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Элемент HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)   
 [Элемент HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Элемент HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md)  
  
  
