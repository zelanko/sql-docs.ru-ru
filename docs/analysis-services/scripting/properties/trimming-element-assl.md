---
title: Элемент trimming (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3273dba26a1b7af45b2a9eed5aab2d6302fa61a1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="trimming-element-assl"></a>Элемент Trimming (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, как выполняется усечение пробелов в данных из источника данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   ...  
   <Trimming>...</Trimming>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Правильно*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Слева*|Данные усекаются слева.|  
|*Правильно*|Данные усекаются справа.|  
|*LeftRight*|Данные усекаются слева и справа.|  
|*None*|Данные не усекаются.|  
  
 Перечисление, соответствующее разрешенным значениям для **Trimming** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Trimming>.  
  
 Элемент, соответствующий родителю параметра **Trimming** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
