---
title: "Элемент ReportParameters (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
apiname: ReportParameters Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ReportParameters
helpviewer_keywords: ReportParameters element
ms.assetid: 0e138e8f-8313-47f2-96e1-cd189eec26bb
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 61b863015757214818a829b1a835e8cbbd41e111
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="reportparameters-element-assl"></a>Элемент ReportParameters (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит коллекцию элементов [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md) элементы для [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action xsi:type="ReportAction">  
   ...  
   <ReportParameters>  
      <ReportParameter>...</ReportParameter>  
   </ReportParameters>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Action](../../../analysis-services/scripting/objects/action-element-assl.md) типа [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)|  
|Дочерние элементы|[ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ReportParameterCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
