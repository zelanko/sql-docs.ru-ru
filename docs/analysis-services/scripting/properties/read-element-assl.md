---
title: Прочитать элемент (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5742e7708158bfb703a5e4de8abcffd52dea67f3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="read-element-assl"></a>Элемент Read (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, можно ли читать данные или метаданные для указанного элемента [CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md) или [Permission](../../../analysis-services/scripting/data-type/permission-data-type-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimensionPermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [Permission](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*None*|Из родительского объекта запрещен доступ к данным и метаданным.|  
|*Допускается*|Доступ для чтения разрешен к данным и метаданным из родительского объекта.|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента **чтения** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeDimensionPermission> и <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Элемент измерения & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Элемент CubePermission & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)   
 [Тип данных Permission & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
