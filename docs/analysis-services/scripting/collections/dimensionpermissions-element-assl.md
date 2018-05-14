---
title: Элемент DimensionPermissions (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4e0b3c04dffb4bae15d54b68f9b4212cfe03200
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="dimensionpermissions-element-assl"></a>Элемент DimensionPermissions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Для элементов **CubePermission** элементы **DimensionPermission** в этой коллекции заменяют разрешения, заданные в коллекции **DimensionPermissions** для каждого измерения, на которое есть явная ссылка. Если в этой коллекции нет ссылки на измерение, то элемент **CubePermission** наследует разрешения, указанные в коллекции **DimensionPermissions** измерения.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DimensionPermissionCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
