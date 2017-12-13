---
title: "Группировать элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Group Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: GROUP
helpviewer_keywords: Group element
ms.assetid: 7df4ba90-b39f-4d8a-8db1-b73639a522a6
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1387b37fec5eff375edf7fc6ba0e506a81854c08
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="group-element-assl"></a>Элемент Group (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет группу элементов, привязанных к атрибуту.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Groups>  
   <Group>  
      <Name>...</Name>  
      <Members>...</Members>  
   </Group>  
<Groups/>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Группы](../../../analysis-services/scripting/collections/groups-element-assl.md)|  
|Дочерние элементы|[Members](../../../analysis-services/scripting/collections/members-element-assl.md), [Name](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Group>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных UserDefinedGroupBinding &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
