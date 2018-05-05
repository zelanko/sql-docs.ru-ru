---
title: Элемент AllowedRowsExpression (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ba13c524d4b78fdc8d17e7c15b285c4c1a22239e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="allowedrowsexpression-element-assl"></a>Элемент AllowedRowsExpression (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
