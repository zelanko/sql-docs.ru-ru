---
title: "Элемент FoldingParameters (ASSL) | Документы Microsoft"
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
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ddfadd34b6d0b0ae7ba459f35ccb7c1fa7faa31a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="foldingparameters-element-assl"></a>Элемент FoldingParameters (ASSL)
  Задает параметры, используемые сервером служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] при перекрестной проверке моделей интеллектуального анализа данных.  
  
> [!NOTE]  
>  Эти параметры предназначены только для внутреннего использования. Эти сведения предоставлены только в информационных целях.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModel>  
   ...  
   <ddl100_100:FoldingParameters>...  
      <ddl100_100:FoldIndex>...</ddl100_100:FoldIndex>  
      <ddl100_100:FoldCount>...</ddl100_100:FoldCount>  
      <ddl100_100:MaxCases>...</ddl100_100:MAxCases>  
      <ddl100_100:FoldTargetAttribute>...</ddl100_100:FoldTargetAttribute  
...</ddl100_100:FoldingParameters>  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|*FoldIndex*|Целое число, указывающее начальную позицию секции, используемой для перекрестной проверки.|  
|*FoldCount*|Целое число, указывающее количество секций в модели после перекрестной проверки.|  
|*MaxCases*|Целое число, указывающее, сколько вариантов модели используется для перекрестной проверки.<br /><br /> Значение 0 указывает, что были использованы все варианты.|  
|*FoldTargetAttribute*|Строка, задающая идентификатор столбца модели, содержащего прогнозируемый атрибут.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Дочерние элементы|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Замечания  
 Эти свойства предназначены только для внутреннего использования, и они не поддерживаются в инструкциях DDL.  
  
 Дополнительные сведения об использовании перекрестной проверки в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], в разделе [меры в отчете перекрестной проверки](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
 Дополнительные сведения о выполнении перекрестной проверки с помощью [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] хранимых процедур [данных интеллектуального анализа данных хранимые процедуры &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41; ](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

