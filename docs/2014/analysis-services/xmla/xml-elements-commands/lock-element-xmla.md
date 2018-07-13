---
title: Заблокировать элемент (XMLA) | Документация Майкрософт
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
- Lock Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 44225f211ac013edd82de08c9ca82f22cb349f96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209874"
---
# <a name="lock-element-xmla"></a>Элемент Lock (XML для аналитики)
  Блокирует указанный объект в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Идентификатор](../xml-elements-properties/id-element-xmla.md), [режим](../xml-elements-properties/mode-element-xmla.md), [объекта](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `Lock` блокирует объект для совместного или монопольного использования в контексте текущей активной транзакции. Явно выполнять команду `Lock` могут только администраторы базы данных или администраторы сервера. Блокировка объекта не позволяет фиксировать транзакции, пока она не будет снята. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают два типа блокировок: совмещаемые и монопольные. Дополнительные сведения о поддерживаемых типах блокировки [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], см. в разделе [элемент Mode &#40;XMLA&#41;](../xml-elements-properties/mode-element-xmla.md).  
  
 Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] позволяют блокировать только базы данных. Элемент `Object` должен содержать ссылку на базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Если элемент `Object` не указан или если элемент `Object` ссылается на объект, отличающийся от базы данных, возникает ошибка.  
  
 Другие команды неявно выполняют команду `Lock` для базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Любая операция по чтению данных или метаданных из базы данных, например любой метод `Discover` или метод `Execute`, запускающий команду `Statement`, неявно устанавливает совмещаемую блокировку для базы данных. Любая транзакция, фиксирующая изменения в данных или метаданных объекта в базе данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], например метод `Execute`, запускающий команду `Alter`, неявно устанавливает монопольную блокировку для базы данных.  
  
 Все блокировки удерживаются в контексте текущей транзакции. После фиксации или отката текущей транзакции все блокировки, определенные в рамках транзакции, автоматически снимаются.  
  
## <a name="see-also"></a>См. также  
 [Разблокировать элемент &#40;XML для Аналитики&#41;](lock-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
