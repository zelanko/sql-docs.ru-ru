---
title: "Доступ к элементу (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Access Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Access
helpviewer_keywords:
- Access element
ms.assetid: 6ad99010-fac5-48e9-a099-ecbca380e127
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f04bafc11cdda8d9c0e82b6cb8dee3e3916099eb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="access-element-assl"></a>Элемент Access (ASSL)
  Указывает уровень доступа для [CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CellPermission>  
   ...  
   <Access>...</Access>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Данный элемент может принимать значение одной из строк, перечисленных в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Чтение*|Допускается доступ только для чтения.|  
|*Производное чтение*|Допускается доступ на производное чтение.|  
|*ReadWrite*|Допускается доступ для чтения и записи.|  
  
 Перечисление, соответствующее разрешенным значениям для **доступа** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CellPermissionAccess>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
