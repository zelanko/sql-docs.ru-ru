---
title: Элемент ScriptCacheProcessingMode (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ScriptCacheProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ScriptCacheProcessingMode
helpviewer_keywords:
- ScriptCacheProcessingMode element
ms.assetid: 95c0723c-69a4-43e7-b743-f712180a7681
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d74499d0678f920fe9f09b9cdc2d8626045a380
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221344"
---
# <a name="scriptcacheprocessingmode-element-assl"></a>Элемент ScriptCacheProcessingMode (ASSL)
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
|Значение по умолчанию|*Регулярные*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Cube](../objects/cube-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Регулярные*|Сервер создает кэш скрипта во время обработки.|  
|*Отложенная*|Сервер создает кэш скрипта после обработки.|  
  
 Перечисление, соответствующее допустимым значениям элемента `ScriptCacheProcessingMode` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ScriptCacheProcessingMode>.  
  
 Элемент, соответствующий родителю параметра `ScriptCacheProcessingMode` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Cube>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
