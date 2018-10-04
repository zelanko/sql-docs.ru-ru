---
title: Элемент FoldingParameters (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5f7f32684686f7b8f12bb147bb4f6b7ea87537e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117428"
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
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|*FoldIndex*|Целое число, указывающее начальную позицию секции, используемой для перекрестной проверки.|  
|*FoldCount*|Целое число, указывающее количество секций в модели после перекрестной проверки.|  
|*MaxCases*|Целое число, указывающее, сколько вариантов модели используется для перекрестной проверки.<br /><br /> Значение 0 указывает, что были использованы все варианты.|  
|*FoldTargetAttribute*|Строка, задающая идентификатор столбца модели, содержащего прогнозируемый атрибут.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Дочерние элементы|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Примечания  
 Эти свойства предназначены только для внутреннего использования, и они не поддерживаются в инструкциях DDL.  
  
 Сведения об использовании перекрестной проверки в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], см. в разделе [меры в отчете перекрестной проверки](../../data-mining/measures-in-the-cross-validation-report.md).  
  
 Сведения о том, как выполнить перекрестную проверку с помощью [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] хранимых процедур см. в разделе [хранимые процедуры интеллектуального анализа &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
