---
title: Элемент StatusGraphic (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- StatusGraphic Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StatusGraphic
helpviewer_keywords:
- StatusGraphic element
ms.assetid: 14b365bc-924d-4791-ad4a-a38155fec42e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98c1b9d076b6ed6981b02b8c4198c330bb0aca53
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190420"
---
# <a name="statusgraphic-element-assl"></a>Элемент StatusGraphic (ASSL)
  Содержит рекомендованное графическое представление состояния [ключевого показателя эффективности](../objects/kpi-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Kpi>  
   ...  
   <StatusGraphic>...</StatusGraphic>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Ключевой показатель эффективности](../objects/kpi-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Светофор - одной*|Светофор (один)|  
|*Светофор - несколько*|Светофор (несколько)|  
|*Дорожные знаки*|Дорожные знаки|  
|*Датчик — по возрастанию*|Датчик|  
|*Датчик — по убыванию*|Обратная шкала|  
|*Термометра*|Термометр|  
|*Цилиндр*|Цилиндр|  
|*Смайлик*|Лицо|  
  
 Элемент, соответствующий родителю параметра `StatusGraphic` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
