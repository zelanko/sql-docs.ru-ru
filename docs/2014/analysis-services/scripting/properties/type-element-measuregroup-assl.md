---
title: Введите элемент (MeasureGroup) (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (MeasureGroup)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 3a584baf-36bb-4e1d-9128-c4758c0b8f06
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f1e583e8debf2f8416ac46574e8c4f5dbc8d4453
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187818"
---
# <a name="type-element-measuregroup-assl"></a>Элемент Type (MeasureGroup) (ASSL)
  Указывает тип [MeasureGroup](../objects/group-element-assl.md).  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Группа мер](../objects/group-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Обычный*|Содержит регулярные меры.|  
|*ExchangeRate*|Содержит меры курсов иностранных валют.|  
|*Продажи*|Содержит меры продаж.|  
|*Бюджета*|Содержит меры бюджета.|  
|*FinancialReporting*|Содержит меры финансовых отчетов.|  
|*Маркетинг*|Содержит меры маркетинга.|  
|*Инвентаризации*|Содержит меры товаров.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Type` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.MeasureGroupType>.  
  
 Элемент, соответствующий родителю параметра `Type` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  