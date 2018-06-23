---
title: Элемент ClassifiedColumnID (ASSL) | Документы Microsoft
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
- ClassifiedColumnID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClassifiedColumnID
helpviewer_keywords:
- ClassifiedColumnID element
ms.assetid: c294b9c5-3ac2-4554-8ba8-d9f15d7e85c0
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: aa8223969facc66d126bcba7c7d74a8056e60f00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110042"
---
# <a name="classifiedcolumnid-element-assl"></a>Элемент ClassifiedColumnID (ASSL)
  Содержит идентификатор (ID) связанного столбца, классифицированного по [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ClassifiedColumns>  
   <ClassifiedColumnID>...</<ClassifiedColumnID>  
</ClassifiedColumns>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ClassifiedColumns](../collections/columns-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ClassifiedColumns` в объектной модели AMO, — это <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Элемент содержимого &#40;ASSL&#41;](content-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  