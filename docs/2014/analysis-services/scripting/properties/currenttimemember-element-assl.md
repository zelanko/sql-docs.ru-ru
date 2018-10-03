---
title: Элемент CurrentTimeMember (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CurrentTimeMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentTimeMember
helpviewer_keywords:
- CurrentTimeMember element
ms.assetid: 2e73009c-9f2b-441c-bdf0-ca19b160da4f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c8016a1fc492225701c4fe47b60796f475a3c401
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119664"
---
# <a name="currenttimemember-element-assl"></a>Элемент CurrentTimeMember (ASSL)
  Определяет текущий элемент измерения времени, связанного с [ключевого показателя эффективности](../objects/kpi-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Kpi>  
   ...  
   <CurrentTimeMember>...</CurrentTimeMember>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Ключевой показатель эффективности](../objects/kpi-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента является многомерная инструкция, вычисление которой приводит к получению единственного члена в измерении времени, используемого для выборки текущего периода при вычислении ключевого показателя эффективности (KPI).  
  
 Элемент, соответствующий родителю параметра `CurrentTimeMember` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
