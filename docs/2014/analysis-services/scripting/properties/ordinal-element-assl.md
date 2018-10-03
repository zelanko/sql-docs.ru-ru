---
title: Элемент Ordinal (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Ordinal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Ordinal
helpviewer_keywords:
- Ordinal element
ms.assetid: 64e68ad5-439c-4c1d-9df4-ee90c56761b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 87957fdfa3adf85081c0a2ca6a6539917b9f9b81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198744"
---
# <a name="ordinal-element-assl"></a>Элемент Ordinal (ASSL)
  Определяет порядковый номер, к которому следует выполнять привязку в таких коллекциях, как коллекции ключей и переводов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Ordinal>...</Ordinal>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|`0`|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AttributeBinding](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `AttributeBinding` и `CubeAttributeBinding` элементов, в который [тип](type-element-binding-assl.md) свойство может принимать значение *ключ* или *перевода* может быть привязан к атрибуту, который в свою очередь привязан к коллекции столбцы данных представление источника. Значение элемента `Ordinal` определяет, к какому столбцу в этой коллекции относятся элементы `AttributeBinding` или `CubeAttributeBinding`.  
  
 Элементы, соответствующие родителям элемента `Ordinal` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AttributeBinding> и <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
