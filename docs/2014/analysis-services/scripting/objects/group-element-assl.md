---
title: Элемент (ASSL) Group | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Group Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- GROUP
helpviewer_keywords:
- Group element
ms.assetid: 7df4ba90-b39f-4d8a-8db1-b73639a522a6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aff5d6304175df936bd775a08bad10a9e178b7c2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059714"
---
# <a name="group-element-assl"></a>Элемент Group (ASSL)
  Определяет группу элементов, привязанных к атрибуту.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Groups>  
   <Group>  
      <Name>...</Name>  
      <Members>...</Members>  
   </Group>  
<Groups/>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Группы](../collections/groups-element-assl.md)|  
|Дочерние элементы|[Members](../collections/members-element-assl.md), [Name](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Group>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных UserDefinedGroupBinding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
