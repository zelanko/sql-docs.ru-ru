---
title: Элемент ScriptCacheProcessingMode (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f014ac1cbad00a077bee80ec6db32d623e155f9d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="scriptcacheprocessingmode-element-assl"></a>Элемент ScriptCacheProcessingMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает, должен ли сервер строить кэш скриптов во время или после обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube>  
   ...  
      <ScriptCacheProcessingMode>...</ScriptCacheProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Regular*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Regular*|Сервер создает кэш скрипта во время обработки.|  
|*Отложенная*|Сервер создает кэш скрипта после обработки.|  
  
 Перечисление, соответствующее разрешенным значениям для **ScriptCacheProcessingMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ScriptCacheProcessingMode>.  
  
 Элемент, соответствующий родителю параметра **ScriptCacheProcessingMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
