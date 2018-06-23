---
title: Элемент collation (ASSL) | Документы Microsoft
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
- Collation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a8d457901781b177b860fdc4592cf87a2ab99456
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189366"
---
# <a name="collation-element-assl"></a>Элемент Collation (ASSL)
  Задает параметры сортировки, применяемые в родительском элементе.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../objects/cube-element-assl.md), [базы данных](../objects/database-element-assl.md), [DataItem](../data-type/dataitem-data-type-assl.md), [измерения](../objects/dimension-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Строка `Collation` состоит из идентификатора локали и флага сравнения, разделенных символом подчеркивания. Например, строка Latin1_General_CI_AS является допустимой.  
  
 Элементы, соответствующие родителям элемента `Collation` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataItem>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel> и <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  