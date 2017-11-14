---
title: "Элемент HoldoutActualSize | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 24a26b453f90fc82e91b1572b0e79af6477caa22
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="holdoutactualsize-element"></a>Элемент HoldoutActualSize
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
  
## <a name="remarks"></a>Замечания  
 Значение для **HoldoutActualSize** зависит от источника данных и значения для [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md), [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md), и [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md). Поэтому значение **HoldoutActualSize** недоступно до после [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] выполняет обработку структуры интеллектуального анализа данных.  
  
 Элемент, соответствующий родителю параметра **HoldoutActualSize** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] инструкций языка сценариев (ASSL), которые содержат один из параметров контрольных **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, или **HoldoutActualSize**, не может использоваться в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Элемент HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)   
 [Элемент HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Элемент HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md)  
  
  

