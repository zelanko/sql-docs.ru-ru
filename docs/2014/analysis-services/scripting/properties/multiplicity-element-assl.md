---
title: Элемент Multiplicity (ASSL) | Документы Microsoft
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
ms.assetid: 441e3829-9009-4b32-a8c6-fa580663387f
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 91ecb8a8b7ada49666d2b6144d1ba258a7c26b58
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195013"
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
|Родительский элемент|[RelationshipEnd](../data-type/relationshipend-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Один*|Это первичное ключевое окончание.|  
|*Многие*|Это окончание внешнего ключа.|  
  
 Перечисление, соответствующее допустимым значениям элемента `role` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Multiplicity>.  
  
  