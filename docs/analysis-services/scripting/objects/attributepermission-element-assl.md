---
title: Элемент AttributePermission (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 09002c565cb9c4d385a42fcc3969ac28f458ed6e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="attributepermission-element-assl"></a>Элемент AttributePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет разрешения членов элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемент имеет атрибуты отдельного измерения в [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributePermissions>  
   <AttributePermission>  
      <AttributeID>...</AttributeID>  
      <Description>...</Description>  
      <DefaultMember>...</DefaultMember>  
            <VisualTotals>...</VisualTotals>  
      <AllowedSet>...</AllowedSet>  
            <DeniedSet>...</DeniedSet>  
      <Annotations>...</Annotations>  
   </AttributePermission>  
</AttributePermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|  
|Дочерние элементы|[AllowedSet](../../../analysis-services/scripting/properties/allowedset-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [DefaultMember](../../../analysis-services/scripting/properties/defaultmember-element-assl.md), [DeniedSet](../../../analysis-services/scripting/properties/deniedset-element-assl.md), [описание ](../../../analysis-services/scripting/properties/description-element-assl.md), [VisualTotals](../../../analysis-services/scripting/properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных CubeDimensionPermission &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
