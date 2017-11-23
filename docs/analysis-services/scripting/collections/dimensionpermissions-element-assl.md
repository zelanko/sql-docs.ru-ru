---
title: "Элемент DimensionPermissions (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
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
apiname: DimensionPermissions Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DimensionPermissions
helpviewer_keywords: DimensionPermissions element
ms.assetid: cb9fdfbf-2118-423b-ba02-fa36813dbea0
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7a3e99a8dc5f0ce6745a224a16bfd97b3c1b1e31
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dimensionpermissions-element-assl"></a>Элемент DimensionPermissions (ASSL)
  Содержит коллекцию разрешений, применимых к [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md) элемент или [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension> <!-- or CubePermission -->  
   ...  
   <DimensionPermissions>  
            <DimensionPermission>...</DimensionPermission> <!-- parent: Dimension -->  
      <!-- or -->  
      <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- parent: CubePermission -->  
      </DimensionPermissions>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Для элементов **CubePermission** элементы **DimensionPermission** в этой коллекции заменяют разрешения, заданные в коллекции **DimensionPermissions** для каждого измерения, на которое есть явная ссылка. Если в этой коллекции нет ссылки на измерение, то элемент **CubePermission** наследует разрешения, указанные в коллекции **DimensionPermissions** измерения.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DimensionPermissionCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
