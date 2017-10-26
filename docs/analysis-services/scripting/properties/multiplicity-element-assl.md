---
title: "Элемент Multiplicity (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 441e3829-9009-4b32-a8c6-fa580663387f
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b69a5fd295ac6107f5469966cb0b4d7329018eee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="multiplicity-element-assl"></a>Элемент Multiplicity (язык ASSL)
  Указывает, относятся ли указанные атрибуты RelationshipEnd к «одной» или к «нескольким» сторонам связи.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEnd>  
   ...  
   <Multiplicity>...</Multiplicity>  
   ...  
</RelationshipEnd>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию||  
|Количество элементов|1. обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Один*|Это первичное ключевое окончание.|  
|*Многие*|Это окончание внешнего ключа.|  
  
 Перечисление, соответствующее разрешенным значениям для **роли** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Multiplicity>.  
  
  

