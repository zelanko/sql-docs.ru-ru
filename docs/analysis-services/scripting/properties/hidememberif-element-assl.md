---
title: "Элемент HideMemberIf (ASSL) | Документы Microsoft"
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
apiname: HideMemberIf Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: HideMemberIf
helpviewer_keywords: HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eefed5009773186d939401a508785abe4f956125
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="hidememberif-element-assl"></a>Элемент HideMemberIf (ASSL)
  Указывает, необходимо ли и когда необходимо скрывать элемент уровня от клиентских приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Никогда не*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Никогда не*|Элементы никогда не скрываются.|  
|*OnlyChildWithNoName*|Элемент скрыт, если он является единственным дочерним элементом родительского элемента и имеет пустое имя.|  
|*OnlyChildWithParentName*|Элемент скрыт, если он является единственным дочерним элементом родительского элемента, а его имя совпадает с именем родительского элемента.|  
|*NoName*|Элемент скрыт, если имеет пустое имя.|  
|*ParentName*|Элемент скрыт, если его имя совпадает с именем родительского элемента.|  
  
## <a name="remarks"></a>Замечания  
 Перечисление, соответствующее разрешенным значениям для **HideMemberIf** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
