---
title: "Элемент AllowedSet (ASSL) | Документы Microsoft"
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
- AllowedSet Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AllowedSet
helpviewer_keywords:
- AllowedSet element
ms.assetid: 4aff2e03-6e1f-4f1a-b99d-d86bba25ab9b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c5b58d9c23ac6305997ff491a9f76371ebd7179
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="allowedset-element-assl"></a>Элемент AllowedSet (ASSL)
  Содержит выражение набора, определяющее набор допустимых разрешений для [роли](../../../analysis-services/scripting/objects/role-element-assl.md) на атрибут.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributePermission>  
      ...  
   <AllowedSet>...</AllowedSet>  
   ...  
</AttributePermission>  
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
|Родительские элементы|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **AllowedSet** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

