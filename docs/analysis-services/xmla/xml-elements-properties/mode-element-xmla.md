---
title: Элемент Mode (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Mode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7ca3048b6d9d36d9dc7b7b921817a3c19b01fdf9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 Родительский **блокировки** элемент использует **режим** элемент для определения типа создаваемой блокировки на объект. Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*CommitShared*|На указанный объект устанавливается совмещаемая блокировка. Для того же объекта могут быть созданы другие совмещаемые блокировки.<br /><br /> Совмещаемая блокировка предотвращает транзакций, содержащих операции записи, такие как [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) выполнение вызова метода [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) команды на указанный объект, зафиксировать, пока совмещаемая блокировка не будет удалена. Совмещаемая блокировка не препятствует транзакций, содержащих операции чтения, таких как [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) вызова метода или **Execute** выполнение вызова метода [инструкции](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) команду, Фиксация.|  
|*CommitExclusive*|На указанный объект устанавливается монопольная блокировка. Другие совмещаемые или монопольные блокировки не могут быть созданы для того же объекта.<br /><br /> Монопольная блокировка исключает возможность фиксации транзакций, содержащих операции чтения или записи для указанного объекта, до снятия монопольной блокировки.|  
  
## <a name="see-also"></a>См. также:  
 [Элемент ID & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Элемент Object & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
