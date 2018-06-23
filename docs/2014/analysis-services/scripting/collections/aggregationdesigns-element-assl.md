---
title: Элемент AggregationDesigns (ASSL) | Документы Microsoft
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
- AggregationDesigns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesigns
helpviewer_keywords:
- AggregationDesigns element
ms.assetid: 7291956a-9c53-41fe-af2e-2418e26956c5
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6dfddae8284e32f08edc4cf1e0868c7c71c97db2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195467"
---
# <a name="aggregationdesigns-element-assl"></a>Элемент AggregationDesigns (ASSL)
  Содержит коллекцию статистических схем, которые можно совместно использовать в разных секциях в базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup>  
   ...  
   <AggregationDesigns>  
      <AggregationDesign>...</AggregationDesign>  
   </AggregationDesigns>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|нет (коллекция)|  
|Значение по умолчанию|нет (коллекция)|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Группа мер](../objects/group-element-assl.md)|  
|Дочерние элементы|[AggregationDesign](../objects/aggregationdesign-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationDesignCollection>.  
  
## <a name="see-also"></a>См. также  
 [Секции элемент &#40;ASSL&#41;](../objects/partition-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  