---
title: Разбивает элемент (ASSL) | Документы Microsoft
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
- Partitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Partitions
helpviewer_keywords:
- Partitions element
ms.assetid: e41c97ca-da44-48e9-a454-d25ee74209fd
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 39e719c6ae4e04e1a05abc42f4290bbf0746e55b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194356"
---
# <a name="partitions-element-assl"></a>Элемент Partitions (ASSL)
  Содержит коллекцию элементов [секции](../objects/partition-element-assl.md) элементы, используемые методом [MeasureGroup](../objects/group-element-assl.md) элемент или коллекцию привязок секций, которые составляют вне строки [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup> <!-- or MeasureGroupBinding -->  
   ...  
   <Partitions>  
      <Partition>...</Partition> <!-- parent: MeasureGroup -->  
      <!-- or -->  
      <Partition xsi:type="PartitionBinding">...</Partition> <!-- parent: MeasureGroupBinding -->  
   </Partitions>  
   ...  
</MeasureGroup>  
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
|Родительские элементы|[Группа мер](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Группа мер](../objects/group-element-assl.md)|[Секция](../objects/partition-element-assl.md)|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Раздел](../objects/partition-element-assl.md) типа [PartitionBinding](../data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.PartitionCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  