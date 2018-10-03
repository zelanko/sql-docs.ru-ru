---
title: Элемент HideMemberIf (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae715268b4b62c88e8d4f660c7d8d1772ccae02c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109004"
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
  
  
