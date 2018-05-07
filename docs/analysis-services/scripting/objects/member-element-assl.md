---
title: Элемент Member (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1001edf8a3dd7cd2b41525c0e23ed07775e51a4e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="member-element-assl"></a>Элемент Member (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит имя элемента [Group](../../../analysis-services/scripting/objects/group-element-assl.md) или [Role](../../../analysis-services/scripting/objects/role-element-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Members>  
   <Member>  
      <Name>...</Name>  
   </Member>  
</Members>  
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
|Родительские элементы|[Члены](../../../analysis-services/scripting/collections/members-element-assl.md)|  
|Дочерние элементы|[Название](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Элементы, соответствующие родителям элемента **член** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Group> и <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>См. также  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
