---
title: Элемент CellPermissions (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CellPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellPermissions
helpviewer_keywords:
- CellPermissions element
ms.assetid: 4a604f2f-f4c3-42bd-a42b-951263942cc6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1a700960586c9cb6e26475ffb0b6b9a52f9939b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133594"
---
# <a name="cellpermissions-element-assl"></a>Элемент CellPermissions (ASSL)
  Содержит коллекцию разрешений для ячеек в связанном [куба](../objects/cube-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubePermission>  
   ...  
   <CellPermissions>  
      <CellPermission>...</CellPermission>  
   </CellPermissions>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Дочерние элементы|[CellPermission](../objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Коллекция может содержать не больше одного `CellPermission` объекта для каждого допустимого значения из [доступа](../properties/access-element-assl.md) элемент.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CellPermissionCollection>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
