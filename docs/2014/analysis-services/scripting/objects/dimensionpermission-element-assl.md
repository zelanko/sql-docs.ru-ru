---
title: Элемент DimensionPermission (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DimensionPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionPermission
helpviewer_keywords:
- DimensionPermission element
ms.assetid: e06efbda-64fd-4dca-a2b5-c8ffbf21512c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 416755e486ce7acadb1ff43926aeeb4b50a56c04
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225974"
---
# <a name="dimensionpermission-element-assl"></a>Элемент DimensionPermission (ASSL)
  Задает разрешения на определенное измерение базы данных или измерение куба, принадлежащие конкретному элементу [Role](role-element-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionPermissions>  
   <DimensionPermission xsi:type="DimensionPermission">...</DimensionPermission> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- ancestor: CubePermission -->  
</DimensionPermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина||  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может появляться один или несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[Dimension](../data-type/permission-data-type-assl.md)|  
|[CubePermission](../data-type/cubedimensionpermission-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionPermissions](../collections/dimensionpermissions-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.DimensionPermission> и <xref:Microsoft.AnalysisServices.CubeDimensionPermission>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
