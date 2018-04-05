---
title: Элемент LastProcessed (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- LastProcessed Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- LastProcessed
helpviewer_keywords:
- LastProcessed element
ms.assetid: df3d1f6f-705c-4408-9eb3-c550a1dec450
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dd61777044ac8746bfe44a881dd2ad3f70a6253a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lastprocessed-element-assl"></a>Элемент LastProcessed (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит отметку времени только для чтения, которая указывает время последней обработки базы данных, содержащей родительский элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
      <LastProcessed>...</LastProcessed>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|DateTime|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../../../analysis-services/scripting/objects/cube-element-assl.md), [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure ](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [Секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сохраняет значение элемента **LastProcessed** элемента. Это значение изменяется только при обработке базы данных, содержащей родительский элемент. Индивидуальная обработка родительского элемента не изменяет значение элемента **LastProcessed** .  
  
 Элементы, соответствующие родителям элемента **LastProcessed** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure>, и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
