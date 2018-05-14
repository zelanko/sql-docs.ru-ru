---
title: Элемент SourceColumnID (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1e10a8fbf92ca8dfd8567aa8c9a014ed6a6629bf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="sourcecolumnid-element-assl"></a>Элемент SourceColumnID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит идентификатор (ID) исходного столбца структуры интеллектуального анализа данных в родительском элементе [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <SourceColumnID>...</SourceColumnID>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение **SourceColumnID** совпадает с идентификатором столбца структуры интеллектуального анализа данных в [столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md) коллекции родительского объекта **MiningStructure**.  
  
 Элемент, соответствующий родителю параметра **SourceColumnID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningModelColumn>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
