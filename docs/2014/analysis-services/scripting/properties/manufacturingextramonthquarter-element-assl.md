---
title: Элемент ManufacturingExtraMonthQuarter (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ManufacturingExtraMonthQuarter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ManufacturingExtraMonthQuarter
helpviewer_keywords:
- ManufacturingExtraMonthQuarter element
ms.assetid: 6e97d92c-dd1e-48f6-a379-c1036c975f9f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1090e5057208a1472cd58dfeddfd83111abd509
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048115"
---
# <a name="manufacturingextramonthquarter-element-assl"></a>Элемент ManufacturingExtraMonthQuarter (ASSL)
  Определяет месяц производственного периода, которому присваивается дополнительный месяц для [TimeBinding](../data-type/binding-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TimeBinding>  
   ...  
   <ManufacturingExtraMonthQuarter>...</ManufacturingExtraMonthQuarter>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Integer (от 1 до 4)|  
|Значение по умолчанию|`4`|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ManufacturingExtraMonthQuarter` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
