---
title: Элемент ReportParameter (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportParameter
helpviewer_keywords:
- ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fdc677b6aabd9d07275b977dd3d3af3145ea00a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093464"
---
# <a name="reportparameter-element-assl"></a>Элемент ReportParameter (ASSL)
  Содержит имя и значение параметра, передаваемое [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] отчета во время выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ReportParameters>  
      <ReportParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportParameter>  
</ReportParameters>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ReportParameters](../collections/reportparameters-element-assl.md)|  
|Дочерние элементы|[Name](../properties/name-element-assl.md), [Value](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Value` должен содержать многомерное выражение.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Элемент Action &#40;ASSL&#41;](action-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
