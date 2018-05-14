---
title: Элемент FoldingParameters (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 51a035c923f1598147c36e4b0860b5ab233577de
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="foldingparameters-element-assl"></a>Элемент FoldingParameters (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Характеристика|Описание|  
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
  
## <a name="remarks"></a>Примечания  
 Эти свойства предназначены только для внутреннего использования, и они не поддерживаются в инструкциях DDL.  
  
 Дополнительные сведения об использовании перекрестной проверки в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], в разделе [меры в отчете перекрестной проверки](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
 Дополнительные сведения о выполнении перекрестной проверки с помощью [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] хранимых процедур [данных интеллектуального анализа данных хранимые процедуры &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
