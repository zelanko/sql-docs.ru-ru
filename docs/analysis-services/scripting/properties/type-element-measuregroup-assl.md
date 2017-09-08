---
title: "Введите элемент (MeasureGroup) (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Type Element (MeasureGroup)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 3a584baf-36bb-4e1d-9128-c4758c0b8f06
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bbe3c541cafb3e4df1a8a1ea7425fd00e1831c7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="type-element-measuregroup-assl"></a>Элемент Type (MeasureGroup) (ASSL)
  Указывает тип [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup>  
   ...  
   <Type>...</Type>  
   ...  
</MeasureGroup>  
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
|Родительский элемент|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Обычный*|Содержит регулярные меры.|  
|*ExchangeRate*|Содержит меры курсов иностранных валют.|  
|*Продажи*|Содержит меры продаж.|  
|*Бюджета*|Содержит меры бюджета.|  
|*FinancialReporting*|Содержит меры финансовых отчетов.|  
|*Маркетинг*|Содержит меры маркетинга.|  
|*Инвентаризации*|Содержит меры товаров.|  
  
 Перечисление, соответствующее разрешенным значениям для **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MeasureGroupType>.  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
