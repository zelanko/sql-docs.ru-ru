---
title: Элемент AggregationUsage (ASSL) | Документы Microsoft
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
- AggregationUsage Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationUsage
helpviewer_keywords:
- AggregationUsage element
ms.assetid: af0c2e7f-b659-4fbf-9b1a-66128db669a2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0cc9d13ed663b92224584ab57f6f467e3a472d8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095537"
---
# <a name="aggregationusage-element-assl"></a>Элемент AggregationUsage (ASSL)
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
|Значение по умолчанию|*По умолчанию*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Полный*|Каждый агрегат для куба должен включать этот атрибут.|  
|*None*|Ни один агрегат для куба не должен включать этот атрибут.|  
|*Без ограничений*|На конструктор статистических схем не налагаются никакие ограничения.|  
|*По умолчанию*|Конструктор статистических схем применяет роль по умолчанию на основании типа атрибута (*Full* для ключей, *Unrestricted* — для остальных).|  
  
 Перечисление, соответствующее допустимым значениям элемента `AggregationUsage` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AggregationUsage>.  
  
## <a name="see-also"></a>См. также  
 [Куб элемент &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  