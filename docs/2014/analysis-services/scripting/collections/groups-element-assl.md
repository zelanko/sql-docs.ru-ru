---
title: Groups (ASSL) элемент | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Groups Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Groups
helpviewer_keywords:
- Groups element
ms.assetid: 62196435-83a8-4a0a-8be1-7dfc986dc6c5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3abad99209bff641ccd1bbd3b52c29f70eab82b0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090844"
---
# <a name="groups-element-assl"></a>Элемент Groups (ASSL)
  Содержит коллекцию групп элементов, привязанных к атрибуту.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Binding xsi:type="UserDefinedGroupBinding">  
   ...  
   <Groups>  
      <Group>...</Group>  
   </Groups>  
   ...  
</Binding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Привязка](../data-type/binding-data-type-assl.md) типа [UserDefinedGroupBinding](../data-type/userdefinedgroupbinding-data-type-assl.md)|  
|Дочерние элементы|[Группирование](../objects/group-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.GroupCollection>.  
  
## <a name="see-also"></a>См. также  
 [Источники данных и привязки &#40;многомерные службы SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
