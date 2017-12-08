---
title: "Элемент TrendGraphic (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: TrendGraphic Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TrendGraphic
helpviewer_keywords: TrendGraphic element
ms.assetid: 7448fd80-3072-4d85-b3a0-6606d1d20885
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 307e3418e86e2f078e5c18ab33cb7f19401ed242
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="trendgraphic-element-assl"></a>Элемент TrendGraphic (ASSL)
  Содержит рекомендованное графическое представление тренда элемента [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Kpi>  
   ...  
   <TrendGraphic>...</TrendGraphic>  
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
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Стандартная стрелка*|Стандартная стрелка|  
|*Стрелка состояния — по возрастанию*|Стрелка состояния|  
|*Стрелка состояния — по убыванию*|Обратная стрелка состояния|  
|*Смайлик*|Лицо|  
  
 Элемент, соответствующий родителю параметра **TrendGraphic** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
