---
title: Элемент Mode (XML для Аналитики) | Документы Microsoft
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
- Mode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5634e273e1708f9de213436e20008cc6874f50a7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195670"
---
# <a name="mode-element-xmla"></a>Элемент Mode (XML для аналитики)
  Определяет режим, который будет использоваться в родительском [блокировки](../xml-elements-commands/lock-element-xmla.md) элемент при создании блокировки на указанный объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
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
|Родительские элементы|[Блокировка](../xml-elements-commands/lock-element-xmla.md), [разблокировки](../xml-elements-commands/unlock-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 В родительском элементе `Lock` элемент `Mode` применяется для определения типа создаваемой блокировки на объект. Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*CommitShared*|На указанный объект устанавливается совмещаемая блокировка. Для того же объекта могут быть созданы другие совмещаемые блокировки.<br /><br /> Совмещаемая блокировка предотвращает транзакций, содержащих операции записи, такие как [Execute](../xml-elements-methods-execute.md) выполнение вызова метода [Alter](../xml-elements-commands/alter-element-xmla.md) команды на указанный объект, зафиксировать, пока совмещаемая блокировка не будет удалена. Совмещаемая блокировка не препятствует транзакций, содержащих операции чтения, таких как [Discover](../xml-elements-methods-discover.md) вызова метода или `Execute` выполнение вызова метода [инструкции](../xml-elements-commands/statement-element-xmla.md) команду фиксации.|  
|*CommitExclusive*|На указанный объект устанавливается монопольная блокировка. Другие совмещаемые или монопольные блокировки не могут быть созданы для того же объекта.<br /><br /> Монопольная блокировка исключает возможность фиксации транзакций, содержащих операции чтения или записи для указанного объекта, до снятия монопольной блокировки.|  
  
## <a name="see-also"></a>См. также  
 [Элемент ID &#40;XML для Аналитики&#41;](id-element-xmla.md)   
 [Объект элемента &#40;XML для Аналитики&#41;](object-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  