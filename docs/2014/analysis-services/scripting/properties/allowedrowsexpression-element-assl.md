---
title: Элемент AllowedRowsExpression (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a23acca8488d5fa747d29338240cf98e0f703ecc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057254"
---
# <a name="allowedrowsexpression-element-assl"></a>Элемент AllowedRowsExpression (ASSL)
  Содержит выражение анализа данных (DAX) логического типа, которое определяет содержание родительского элемента.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для `CellPermission` элемент, `Expression` элемент содержит логическое Многомерное выражение, определяющее ячейки, применимые к правами, указанными в [доступа](access-element-assl.md) элемент `CellPermission` элемент. Если значение элемента `Expression` для элемента `CellPermission` пусто, то элемент `CellPermission` не учитывается.  
  
 Для элемента `StandardAction` элемент `Expression` содержит многомерное выражение, представляющее содержимое действия. Если значение элемента `Expression` для элемента `StandardAction` пусто, то элемент `StandardAction` не учитывается.  
  
 Родителям в модели объектов AMO соответствуют элементы <xref:Microsoft.AnalysisServices.CellPermission> и <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
