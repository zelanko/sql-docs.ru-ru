---
title: Элемент Ordinal (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88c2409d42fc23f017989218d8ea87172d1b8d3d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="ordinal-element-assl"></a>Элемент Ordinal (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет порядковый номер, к которому следует выполнять привязку в таких коллекциях, как коллекции ключей и переводов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Ordinal>...</Ordinal>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|**0**|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md), [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **AttributeBinding** и **CubeAttributeBinding** элементов, в который [тип](../../../analysis-services/scripting/properties/type-element-binding-assl.md) свойство может принимать значение *ключ* или *перевода* могут быть привязаны к атрибуту, который в свою очередь привязан к коллекции столбцов в представлении источника данных. Значение элемента **Ordinal** определяет, к какому столбцу в этой коллекции относятся элементы **AttributeBinding** или **CubeAttributeBinding** .  
  
 Элементы, соответствующие родителям элемента **порядковый номер** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributeBinding> и <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
