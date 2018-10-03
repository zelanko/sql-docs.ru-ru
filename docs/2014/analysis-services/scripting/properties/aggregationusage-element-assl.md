---
title: Элемент AggregationUsage (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f2673a9747aee6192ac41d6c6e2c446045c4965f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174244"
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
|*Неограниченный*|На конструктор статистических схем не налагаются никакие ограничения.|  
|*По умолчанию*|Конструктор статистических схем применяет роль по умолчанию на основании типа атрибута (*Full* для ключей, *Unrestricted* — для остальных).|  
  
 Перечисление, соответствующее допустимым значениям элемента `AggregationUsage` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AggregationUsage>.  
  
## <a name="see-also"></a>См. также  
 [Элемент куба &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
