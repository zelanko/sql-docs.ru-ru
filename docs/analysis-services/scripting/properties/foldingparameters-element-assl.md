---
title: Элемент FoldingParameters (ASSL) | Документы Microsoft
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
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8f6fa2a178bc1d8f9722a101d7305cedfa248663
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="foldingparameters-element-assl"></a>Элемент FoldingParameters (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Указывает параметры, используемые [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сервера при выполнении перекрестной проверки моделей интеллектуального анализа данных.  
  
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
  
## <a name="remarks"></a>Remarks  
 Эти свойства предназначены только для внутреннего использования, и они не поддерживаются в инструкциях DDL.  
  
 Дополнительные сведения об использовании перекрестной проверки в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], в разделе [меры в отчете перекрестной проверки](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
 Дополнительные сведения о выполнении перекрестной проверки с помощью [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] хранимых процедур [данных интеллектуального анализа данных хранимые процедуры &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41; ](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
