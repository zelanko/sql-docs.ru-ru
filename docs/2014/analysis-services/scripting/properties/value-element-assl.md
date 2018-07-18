---
title: Значение элемента (ASSL) | Документация Майкрософт
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
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5bdf16f2f9ce7415d396cf5f4110fd3127e04774
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201994"
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
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Любой тип simpleType|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Любой тип simpleType|  
|Все остальные|String|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [заметки](../objects/annotation-element-assl.md), [ключевого показателя эффективности](../objects/kpi-element-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Value` содержит значение, связанное с родительским объектом. Ожидаемое значение элемента `Value` зависит от родительского элемента, как описано в следующей таблице.  
  
|Родительский элемент|Ожидаемое значение|  
|--------------------|--------------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Значение параметра алгоритма.|  
|[Заметки](../objects/annotation-element-assl.md)|Значение заметки.|  
|[Ключевой показатель эффективности](../objects/kpi-element-assl.md)|Многомерное выражение, используемое для вычисления значения ключевого показателя эффективности.|  
|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|Значение параметра форматирования отчета.|  
|[ReportParameter](../objects/reportparameter-element-assl.md)|Многомерное выражение, используемое для вычисления значения параметра отчета.|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Значение свойства сервера для текущего запущенного экземпляра.|  
  
 Элементы, соответствующие родителям элемента `Value` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter> и <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
