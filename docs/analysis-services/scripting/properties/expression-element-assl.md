---
title: "Элемент Expression (ASSL) | Документы Microsoft"
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
apiname: Expression Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Expression
helpviewer_keywords: Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7970b30df780502bf17bc053f7d43a94c74634de
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="expression-element-assl"></a>Элемент Expression (ASSL)
  Содержит многомерное выражение, определяющее содержимое родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Для **CellPermission** элемент, **выражение** элемент содержит логическое Многомерное выражение, идентифицирующее ячейки, применимые к правами, указанными в [доступа](../../../analysis-services/scripting/properties/access-element-assl.md) элемент **CellPermission** элемента. Если значение **выражение** элемент для **CellPermission** элемент пуст, **CellPermission** элемент игнорируется.  
  
 Для **StandardAction** элемент, **выражение** элемент содержит Многомерное выражение, представляющее содержимое действия. Если значение **выражение** элемент для **StandardAction** элемент пуст, **StandardAction** элемент игнорируется.  
  
 Родителям в модели объектов AMO соответствуют элементы <xref:Microsoft.AnalysisServices.CellPermission> и <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
