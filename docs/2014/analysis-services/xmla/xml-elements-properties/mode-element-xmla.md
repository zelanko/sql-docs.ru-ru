---
title: Элемент Mode (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e768d9ef176a05d4fe7622a520c9ac98f1d71d81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072414"
---
# <a name="mode-element-xmla"></a>Элемент Mode (XML для аналитики)
  Указывает режим, используемый в родительском [блокировки](../xml-elements-commands/lock-element-xmla.md) элемент при создании блокировки на указанный объект.  
  
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
|*CommitShared*|На указанный объект устанавливается совмещаемая блокировка. Для того же объекта могут быть созданы другие совмещаемые блокировки.<br /><br /> Совмещаемая блокировка предотвращает транзакций, содержащих операции записи, такие как [Execute](../xml-elements-methods-execute.md) выполнение вызова метода [Alter](../xml-elements-commands/alter-element-xmla.md) команды с указанным объектом, фиксации, пока совмещаемая блокировка не будет удалена. Совмещаемая блокировка не предотвращает транзакций, содержащих операции чтения, таких как [Discover](../xml-elements-methods-discover.md) вызов метода или `Execute` выполнение вызова метода [инструкции](../xml-elements-commands/statement-element-xmla.md) команду фиксации.|  
|*CommitExclusive*|На указанный объект устанавливается монопольная блокировка. Другие совмещаемые или монопольные блокировки не могут быть созданы для того же объекта.<br /><br /> Монопольная блокировка исключает возможность фиксации транзакций, содержащих операции чтения или записи для указанного объекта, до снятия монопольной блокировки.|  
  
## <a name="see-also"></a>См. также  
 [Элемент ID &#40;XML для Аналитики&#41;](id-element-xmla.md)   
 [Объект элемента &#40;XML для Аналитики&#41;](object-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
