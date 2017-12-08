---
title: "Срез элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Slice Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Slice
helpviewer_keywords: Slice element
ms.assetid: 2c8c4107-c641-4724-bfa5-0c47e0ec8888
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d15321ca78240bd820ec5e3c625c558986d64f2e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="slice-element-assl"></a>Элемент Slice (ASSL)
  Содержит многомерное выражение, которое определяет срез, содержащийся в секции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Partition>  
      ...  
   <Slice>...</Slice>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **Slice** содержит многомерное выражение кортежа или выражение набора, обозначающее ту часть куба, информация для которой хранится в секции. Многомерное выражение аналогично [StrToSet](../../../mdx/strtoset-mdx.md) MDX-функцию с ключевым словом CONSTRAINED тем, что выражение не может содержать многомерных Выражений или определяемые пользователем функции.  
  
 Элемент, соответствующий родителю параметра **срез** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
