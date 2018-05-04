---
title: Элемент StopTime (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- StopTime Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- StopTime
helpviewer_keywords:
- StopTime element
ms.assetid: 6f863d53-033b-46e0-9837-e891e739b4b0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2a7b5728187d46d03fc8cdbbbcd10ad49656e282
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stoptime-element-assl"></a>Элемент StopTime (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает дату и время, когда [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md) остановки элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
   ...  
   <StopTime>...</StopTime>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|DateTime|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Дочерние элементы|Нет|  
  
 Элемент, соответствующий родителю параметра **StopTime** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также  
 [Элемент traces & #40; ASSL & #41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
