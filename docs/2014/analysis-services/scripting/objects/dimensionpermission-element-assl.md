---
title: Элемент DimensionPermission (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 66d9c86c065bb57735e6d54f6d6fc6f30b2d48a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101398"
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
  
  