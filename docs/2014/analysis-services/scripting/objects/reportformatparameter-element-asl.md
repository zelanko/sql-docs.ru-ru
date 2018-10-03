---
title: Элемент ReportFormatParameter (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportFormatParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameter
helpviewer_keywords:
- ReportFormatParameter element
ms.assetid: 064a8683-c44b-4261-be4d-32226d3d3119
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f3dd567a88a76837e13d051988620eb1886ef40
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188024"
---
# <a name="reportformatparameter-element-assl"></a>Элемент ReportFormatParameter (ASSL)
  Содержит имя и значение параметра, который указывает, каким образом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] форматирования отчета во время выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ReportFormatParameters>  
   <ReportFormatParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportFormatParameter>  
</ReportFormatParameters>  
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
|Родительский элемент|[ReportFormatParameters](../collections/reportformatparameters-element-assl.md)|  
|Дочерние элементы|[Name](../properties/name-element-assl.md), [Value](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ReportFormatParameter` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ReportAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Элемент Action &#40;ASSL&#41;](action-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
