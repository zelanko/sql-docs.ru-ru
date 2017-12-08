---
title: "Значение элемента (ASSL) | Документы Microsoft"
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
apiname: Value Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Value
helpviewer_keywords: Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eda952daf69b54246aa095fde0c187adfbbbc5e0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="value-element-assl"></a>Элемент Value (ASSL)
  Содержит значение родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AlgorithmParameter> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Value>...</Value>  
   ...  
</AlgorithmParameter>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|См. в следующей таблице.|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|Любой тип simpleType|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|Любой тип simpleType|  
|Все остальные|Строковые значения|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md), [заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md), [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md), [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md), [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md), [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Значение** элемент содержит значение, связанное с родительским объектом. Ожидаемое значение **значение** элемента зависит от родительского элемента, как описано в следующей таблице.  
  
|Родительский элемент|Ожидаемое значение|  
|--------------------|--------------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|Значение параметра алгоритма.|  
|[Заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md)|Значение заметки.|  
|[Ключевой показатель эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md)|Многомерное выражение, используемое для вычисления значения ключевого показателя эффективности.|  
|[ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)|Значение параметра форматирования отчета.|  
|[ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|Многомерное выражение, используемое для вычисления значения параметра отчета.|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|Значение свойства сервера для текущего запущенного экземпляра.|  
  
 Элементы, соответствующие родителям элемента **значение** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter>, и <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
