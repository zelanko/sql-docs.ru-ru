---
title: Элемент HideMemberIf (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- HideMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8633089920469efd8745805d67f3d97e20a41f2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="hidememberif-element-assl"></a>Элемент HideMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Значение|Описание|  
|-----------|-----------------|  
|*Никогда не*|Элементы никогда не скрываются.|  
|*OnlyChildWithNoName*|Элемент скрыт, если он является единственным дочерним элементом родительского элемента и имеет пустое имя.|  
|*OnlyChildWithParentName*|Элемент скрыт, если он является единственным дочерним элементом родительского элемента, а его имя совпадает с именем родительского элемента.|  
|*NoName*|Элемент скрыт, если имеет пустое имя.|  
|*ParentName*|Элемент скрыт, если его имя совпадает с именем родительского элемента.|  
  
## <a name="remarks"></a>Замечания  
 Перечисление, соответствующее разрешенным значениям для **HideMemberIf** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
