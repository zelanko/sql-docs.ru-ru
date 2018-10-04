---
title: Аудит элемент (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Audit Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Audit
helpviewer_keywords:
- Audit element
ms.assetid: 26488119-6490-426d-a4e4-274b5bdffbc2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 283be4682a7dd5742b93cba596efc87322a1d539
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097438"
---
# <a name="audit-element-assl"></a>Элемент Audit (ASSL)
  Указывает, что [трассировки](../objects/trace-element-assl.md) элемент не может удалять любые события, даже если это приводит к снижению производительности на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
   ...  
   <Audit>...</Audit>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|`False`|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Trace](../objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Audit` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также  
 [Выполняет трассировку элемент &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
