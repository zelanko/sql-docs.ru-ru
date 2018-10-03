---
title: Введите элемент (Action) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af38eb6a60e8e54ecfc4ac5bb4fb05faeab69feb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168424"
---
# <a name="type-element-action-assl"></a>Элемент Type (Action) (ASSL)
  Содержит тип [действие](../objects/action-element-assl.md) элемент.  
  
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
|*Детализация*|Получает набор строк для детализации.<br /><br /> Это значение идентично *набора строк* и определяет действия детализации. Это может быть только используемые в операциях, [TargetType](targettype-element-assl.md) присваивается значение *ячеек*.|  
|*Набор данных*|Извлекает набор данных.|  
|*Функции набора строк*|Извлекает набор строк.|  
|*commandLine*|Выполняет команду в командной строке.|  
|*Защищенные авторским правом*|Выполняет операцию с помощью интерфейса, отличного от перечисленного ранее в этой таблице.|  
|*Отчет*|Отображает страницу переменных в интернет-браузере.<br /><br /> Это значение идентично *URL-адрес* и определяет действия с отчетом.|  
  
 Элемент, соответствующий родителю параметра `Type` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных DrillThroughAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Тип данных ReportAction &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
