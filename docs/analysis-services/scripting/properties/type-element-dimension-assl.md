---
title: "Тип элемента (измерение) (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element (Dimension)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f11755a12e1876c1883b08f2460a7d8cc264dc25
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="type-element-dimension-assl"></a>Элемент Type (Dimension) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет сведения о содержимом измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Обычный*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Некоторые значения элемента **Type**, например *Accounts*, определяют особое поведение.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Обычный*|Измерение является обычным измерением.|  
|*Time*|Измерение является измерением времени.<br /><br /> Примечание: Это значение указывает, что измерение поддерживает функциональные возможности, специфичные для измерений времени.|  
|*Geography*|Измерение содержит географические атрибуты.|  
|*Организации*|Измерение содержит организационные атрибуты.|  
|*Измерение ведомости материалов*|Измерение содержит атрибуты ведомости материалов.|  
|*Измерение счетов*|Измерение содержит атрибуты, связанные со счетом.<br /><br /> Примечание: Это значение указывает, что измерение поддерживает функциональные возможности, специфичные для измерений счетов.|  
|*Клиенты*|Измерение содержит атрибуты, связанные с пользователем.|  
|*Продукты*|Измерение содержит атрибуты, связанные с продуктом.|  
|*Сценарий*|Измерение содержит атрибуты, связанные со сценарием.|  
|*Количественное*|Измерение содержит количественные атрибуты.|  
|*Служебная программа*|Измерение содержит вспомогательные атрибуты.|  
|*Валюта*|Измерение содержит атрибуты валюты.|  
|*Курсы*|Измерение содержит атрибуты обменного курса.|  
|*Channel*|Измерение содержит атрибуты канала.|  
|*Повышение роли*|Измерение содержит атрибуты, связанные с продвижением.|  
  
 Перечисление, соответствующее разрешенным значениям для **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionType>.  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
