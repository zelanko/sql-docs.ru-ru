---
title: Группирует элемент (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 886263a1470d8ebc0c45cc6022e087ee434c3ff6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="groups-element-assl"></a>Элемент Groups (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит коллекцию групп элементов, привязанных к атрибуту.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Binding xsi:type="UserDefinedGroupBinding">  
   ...  
   <Groups>  
      <Group>...</Group>  
   </Groups>  
   ...  
</Binding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Привязка](../../../analysis-services/scripting/data-type/binding-data-type-assl.md) типа [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|Дочерние элементы|[Группирование](../../../analysis-services/scripting/objects/group-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.GroupCollection>.  
  
## <a name="see-also"></a>См. также  
 [Источники данных и привязки &#40;многомерные службы SSAS&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
