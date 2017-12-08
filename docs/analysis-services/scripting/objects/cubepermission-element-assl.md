---
title: "Элемент CubePermission (ASSL) | Документы Microsoft"
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
apiname: CubePermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CubePermission
helpviewer_keywords: CubePermission element
ms.assetid: b144b623-ff20-4ead-91ad-4c718f3b140b
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d91b2d7aa82ccc9e6158d592b6fa1e428f109b6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cubepermission-element-assl"></a>Элемент CubePermission (ASSL)
  Определяет разрешения элементов конкретного [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента в указанном [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubePermissions>  
   <CubePermission>  
      <!-- The following elements extend Permission -->  
      <ReadSourceData>...</ReadSourceData>  
            <DimensionPermissions>...</DimensionPermissions>  
            <CellPermissions>...</CellPermissions>  
   </CubePermission>  
</CubePermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|0-n: необязательный элемент, который может появляться один или несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubePermissions](../../../analysis-services/scripting/collections/cubepermissions-element-assl.md)|  
|Дочерние элементы|[CellPermissions](../../../analysis-services/scripting/collections/cellpermissions-element-assl.md), [DimensionPermissions](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md), [ReadSourceData](../../../analysis-services/scripting/properties/readsourcedata-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CUBE &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
