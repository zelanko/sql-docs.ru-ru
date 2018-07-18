---
title: Элемент Mode (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 12e792c51b2f6feb3edb4e01c12dcf4809e2d4d4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575756"
---
# <a name="mode-element-xmla"></a>Элемент Mode (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет режим, который будет использоваться в родительском [блокировки](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) элемент при создании блокировки на указанный объект.  
  
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
|Родительские элементы|[Блокировка](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [разблокировки](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Родительский **блокировки** элемент использует **режим** элемент для определения типа создаваемой блокировки на объект. Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*CommitShared*|На указанный объект устанавливается совмещаемая блокировка. Для того же объекта могут быть созданы другие совмещаемые блокировки.<br /><br /> Совмещаемая блокировка предотвращает транзакций, содержащих операции записи, такие как [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) выполнение вызова метода [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) команды на указанный объект, зафиксировать, пока совмещаемая блокировка не будет удалена. Совмещаемая блокировка не препятствует транзакций, содержащих операции чтения, таких как [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) вызова метода или **Execute** выполнение вызова метода [инструкции](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) команду, Фиксация.|  
|*CommitExclusive*|На указанный объект устанавливается монопольная блокировка. Другие совмещаемые или монопольные блокировки не могут быть созданы для того же объекта.<br /><br /> Монопольная блокировка исключает возможность фиксации транзакций, содержащих операции чтения или записи для указанного объекта, до снятия монопольной блокировки.|  
  
## <a name="see-also"></a>См. также
 [Элемент ID &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Объект элемента &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
