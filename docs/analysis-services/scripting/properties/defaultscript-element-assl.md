---
title: Элемент DefaultScript (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e21b89833edf744a6e47474e9c438be74530479c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
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
  
  
