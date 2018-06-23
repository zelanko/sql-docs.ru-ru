---
title: Элемент StatusGraphic (ASSL) | Документы Microsoft
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
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c551e084d833dff17b7d6c1ab46b398cf6f62313
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192525"
---
# <a name="statusgraphic-element-assl"></a>Элемент StatusGraphic (ASSL)
  Содержит рекомендованное графическое представление состояния [ключевого показателя эффективности](../objects/kpi-element-assl.md) элемента.  
  
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
|*Светофор - один*|Светофор (один)|  
|*Светофор - несколько*|Светофор (несколько)|  
|*Дорожные знаки*|Дорожные знаки|  
|*Датчик — по возрастанию*|Датчик|  
|*Датчик — по убыванию*|Обратная шкала|  
|*Термометр*|Термометр|  
|*Цилиндр*|Цилиндр|  
|*Смайлик*|Лицо|  
  
 Элемент, соответствующий родителю параметра `StatusGraphic` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  