---
title: Элемент AggregationUsage (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2086a274fb76238efd11e4f7c881b07f0b98159f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationusage-element-assl"></a>Элемент AggregationUsage (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элементы управления как конструктор статистических схем в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] статистических схем.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeAttribute>  
   ...  
   <AggregationUsage>...</AggregationUsage>  
   ...  
</CubeAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Default*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Полный*|Каждый агрегат для куба должен включать этот атрибут.|  
|*None*|Ни один агрегат для куба не должен включать этот атрибут.|  
|*Без ограничений*|На конструктор статистических схем не налагаются никакие ограничения.|  
|*Default*|Конструктор статистических схем применяет роль по умолчанию на основании типа атрибута (*Full* для ключей, *Unrestricted* — для остальных).|  
  
 Перечисление, соответствующее разрешенным значениям для **AggregationUsage** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationUsage>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
