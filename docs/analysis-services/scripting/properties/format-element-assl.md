---
title: Форматировать элемент (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 34220d27f4a0ca1f30b67b5066f5a06877816652
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="format-element-assl"></a>Элемент Format (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит требуемый формат параметра [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
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
|Родительский элемент|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Допустимыми значениями для элемента **Format** являются форматы Microsoft Office Excel, а также строки *TrimRight*, *TrimLeft*, *TrimAll*и *TrimNone*. Для усечения значением по умолчанию является значение *TrimRight* .  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Строка в любом формате Excel|Данные форматируются в соответствии с указанной именованной или пользовательской строкой форматирования. Любая строка форматирования, которую поддерживает Excel, может быть предоставлена.|  
|*TrimAll*|Данные усекаются слева и справа.|  
|*TrimLeft*|Данные усекаются слева.|  
|*TrimNone*|Данные не усекаются.|  
|*TrimRight*|Данные усекаются справа.|  
  
 Элемент, соответствующий родителю параметра **формат** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
