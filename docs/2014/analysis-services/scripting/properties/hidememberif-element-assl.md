---
title: Элемент HideMemberIf (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- HideMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2b1540a3b7f5d1e1a93ea3b4628bfbde186e5bb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101145"
---
# <a name="hidememberif-element-assl"></a>Элемент HideMemberIf (ASSL)
  Указывает, необходимо ли и когда необходимо скрывать элемент уровня от клиентских приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Никогда не*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Level](../objects/level-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Никогда не*|Элементы никогда не скрываются.|  
|*OnlyChildWithNoName*|Элемент скрыт, если он является единственным дочерним элементом родительского элемента и имеет пустое имя.|  
|*OnlyChildWithParentName*|Элемент скрыт, если он является единственным дочерним элементом родительского элемента, а его имя совпадает с именем родительского элемента.|  
|*NoName*|Элемент скрыт, если имеет пустое имя.|  
|*ParentName*|Элемент скрыт, если его имя совпадает с именем родительского элемента.|  
  
## <a name="remarks"></a>Примечания  
 Перечисление, соответствующее допустимым значениям элемента `HideMemberIf` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  