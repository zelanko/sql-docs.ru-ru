---
title: Элемент trimming (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Trimming Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Trimming
helpviewer_keywords:
- Trimming element
ms.assetid: 8b3bbf89-8309-4d00-9aea-a5918f0c7027
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 250394f67c79eec799f75dd0b6f590f6bff8f988
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198785"
---
# <a name="trimming-element-assl"></a>Элемент Trimming (ASSL)
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Слева*|Данные усекаются слева.|  
|*Правильно*|Данные усекаются справа.|  
|*LeftRight*|Данные усекаются слева и справа.|  
|*None*|Данные не усекаются.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Trimming` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Trimming>.  
  
 Элемент, соответствующий родителю параметра `Trimming` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
