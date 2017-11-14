---
title: "Введите элемент (Action) (ASSL) | Документы Microsoft"
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
apiname:
- Type Element (Action)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62735cdcc160bccf6b90ed2c26b269b8b3d1d3eb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="type-element-action-assl"></a>Элемент Type (Action) (ASSL)
  Содержит тип [действия](../../../analysis-services/scripting/objects/action-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*URL-адрес*|Отображает страницу переменных в интернет-браузере.|  
|*HTML*|Выполняет HTML-скрипт в браузере Интернета.|  
|*Инструкция*|Выполняет команду OLE DB.|  
|*Детализация*|Получает набор строк для детализации.<br /><br /> Это значение идентично *строк* и определяет действия детализации. Это может быть только используется в операциях, чей [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) имеет значение *ячейки*.|  
|*Набор данных*|Извлекает набор данных.|  
|*Набор строк*|Извлекает набор строк.|  
|*Командная строка*|Выполняет команду в командной строке.|  
|*Частные*|Выполняет операцию с помощью интерфейса, отличного от перечисленного ранее в этой таблице.|  
|*Отчет*|Отображает страницу переменных в интернет-браузере.<br /><br /> Это значение идентично *URL-адрес* и определяет действия с отчетом.|  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных DrillThroughAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [Тип данных ReportAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

