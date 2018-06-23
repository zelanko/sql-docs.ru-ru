---
title: Элемент Members (ASSL) | Документы Microsoft
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
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Members
helpviewer_keywords:
- Members element
ms.assetid: 4bf585a3-b681-486d-852b-1244c5658a04
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 45b1dea7d3d3bee599f73b0fc0110933eb0cc363
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098057"
---
# <a name="members-element-assl"></a>Элемент Members (ASSL)
  Содержит коллекцию элементов [Member](../objects/member-element-assl.md) для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Group> <!-- or Role --<  
   ...  
   <Members>  
      <Member>...</Member>  
   </Members>  
   ...  
</Group>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Group](../objects/group-element-assl.md), [Role](../objects/role-element-assl.md)|  
|Дочерние элементы|[Член](../objects/member-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента `Members` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Group> и <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  