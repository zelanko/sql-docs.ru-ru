---
title: Элемент Text (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Text Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- text
helpviewer_keywords:
- Text element
ms.assetid: 0edece73-236f-4661-8102-3fcc29326bf4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a53693bc2a102061c84e7c44c4155c21adb51756
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057804"
---
# <a name="text-element-assl"></a>Элемент Text (ASSL)
  Содержит текст [команда](../objects/command-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Text>...</Text>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Command](../objects/command-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Text` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Command>.  
  
## <a name="see-also"></a>См. также  
 [Команды элемент &#40;ASSL&#41;](../collections/commands-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
