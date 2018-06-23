---
title: Введите элемент (Action) (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d71abdd26cea5fa03c8e70f882f893878a70969a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100700"
---
# <a name="type-element-action-assl"></a>Элемент Type (Action) (ASSL)
  Содержит тип [действия](../objects/action-element-assl.md) элемента.  
  
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
|Родительский элемент|[Действие](../objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*URL-адрес*|Отображает страницу переменных в интернет-браузере.|  
|*HTML*|Выполняет HTML-скрипт в браузере Интернета.|  
|*Инструкция*|Выполняет команду OLE DB.|  
|*Детализация*|Получает набор строк для детализации.<br /><br /> Это значение идентично *строк* и определяет действия детализации. Это может быть только используется в операциях, чей [TargetType](targettype-element-assl.md) имеет значение *ячейки*.|  
|*Набор данных*|Извлекает набор данных.|  
|*Функции набора строк*|Извлекает набор строк.|  
|*Командная строка*|Выполняет команду в командной строке.|  
|*Частные*|Выполняет операцию с помощью интерфейса, отличного от перечисленного ранее в этой таблице.|  
|*Отчет*|Отображает страницу переменных в интернет-браузере.<br /><br /> Это значение идентично *URL-адрес* и определяет действия с отчетом.|  
  
 Элемент, соответствующий родителю параметра `Type` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных DrillThroughAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Тип данных ReportAction &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  