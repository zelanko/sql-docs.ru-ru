---
title: Введите элемент (Action) (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8b87ab109aaad0c40e1debb3a8ea84047b6e8f6b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-action-assl"></a>Элемент Type (Action) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Значение|Описание|  
|-----------|-----------------|  
|*URL-адрес*|Отображает страницу переменных в интернет-браузере.|  
|*HTML*|Выполняет HTML-скрипт в браузере Интернета.|  
|*Инструкция*|Выполняет команду OLE DB.|  
|*Детализация*|Получает набор строк для детализации.<br /><br /> Это значение идентично *строк* и определяет действия детализации. Это может быть только используется в операциях, чей [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) имеет значение *ячейки*.|  
|*набор данных*|Извлекает набор данных.|  
|*Функции набора строк*|Извлекает набор строк.|  
|*Командная строка*|Выполняет команду в командной строке.|  
|*Частные*|Выполняет операцию с помощью интерфейса, отличного от перечисленного ранее в этой таблице.|  
|*Отчет*|Отображает страницу переменных в интернет-браузере.<br /><br /> Это значение идентично *URL-адрес* и определяет действия с отчетом.|  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных DrillThroughAction &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [Тип данных ReportAction &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
