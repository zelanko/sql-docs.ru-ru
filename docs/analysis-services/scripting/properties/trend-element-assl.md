---
title: Тренд элемент (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 95f57ed8818f7d094ed8da199aa6ea79d5476cf7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="trend-element-assl"></a>Элемент Trend (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит выражение многомерных выражений (MDX), возвращающее Признак тренда [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Kpi>  
   ...  
   <Trend>...</Trend>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Ключевой показатель эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент **Trend** содержит многомерное выражение, результатом вычисления которого является число от -1 до 1.  
  
 Элемент, соответствующий родителю параметра **тренда** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
