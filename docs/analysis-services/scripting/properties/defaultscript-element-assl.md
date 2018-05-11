---
title: Элемент DefaultScript (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8b0a89ee60b18c25941a6e33898898c4bfa5ca20
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="defaultscript-element-assl"></a>Элемент DefaultScript (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет значение по умолчанию [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) элемент в [MdxScripts](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MdxScript>  
   ...  
   <DefaultScript>...</DefaultScript>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|**True**|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Присвоение элементу **DefaultScript** значения **True** для одного скрипта приводит к присвоению элементу **DefaultScript** значения **False** для всех остальных элементов **MdxScript** в коллекции **MdxScripts** .  
  
 Элемент, соответствующий родителю параметра **DefaultScript** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
