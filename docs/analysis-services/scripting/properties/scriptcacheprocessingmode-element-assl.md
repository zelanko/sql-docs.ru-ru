---
title: Элемент ScriptCacheProcessingMode (ASSL) | Документы Microsoft
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
apiname:
- ScriptCacheProcessingMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ScriptCacheProcessingMode
helpviewer_keywords:
- ScriptCacheProcessingMode element
ms.assetid: 95c0723c-69a4-43e7-b743-f712180a7681
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6a0430d99739470b46399b7ddef28bc7a13d0370
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="scriptcacheprocessingmode-element-assl"></a>Элемент ScriptCacheProcessingMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Указывает, должен ли сервер строить кэш скриптов во время обработки или после обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube>  
   ...  
      <ScriptCacheProcessingMode>...</ScriptCacheProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Обычный*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Обычный*|Сервер создает кэш скрипта во время обработки.|  
|*Отложенная*|Сервер создает кэш скрипта после обработки.|  
  
 Перечисление, соответствующее разрешенным значениям для **ScriptCacheProcessingMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ScriptCacheProcessingMode>.  
  
 Элемент, соответствующий родителю параметра **ScriptCacheProcessingMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
