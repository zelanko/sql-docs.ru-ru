---
title: Элемент ReportParameter (ASSL) | Документы Microsoft
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
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 58aeafeaee114c1d08d0ad8b0119bee2dc5d5dea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101833"
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
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Элемент Action &#40;ASSL&#41;](action-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  