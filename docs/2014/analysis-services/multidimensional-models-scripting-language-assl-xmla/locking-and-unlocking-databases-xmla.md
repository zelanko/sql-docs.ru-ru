---
title: Блокировка и снятие блокировки баз данных (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 120326066a9145c6e223f9af5735c4b3435222c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219504"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Блокировка и снятие блокировки баз данных (XMLA)
  Блокировка и снятие блокировки баз данных с помощью, соответственно, [блокировки](../xmla/xml-elements-commands/lock-element-xmla.md) и [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) команды в XML для аналитики (XMLA). Другие команды XML для аналитики также при необходимости автоматически блокируют и снимают блокировку объектов в процессе выполнения команды. Можно явно блокировать или разблокировать базу данных для выполнения нескольких команд в одной транзакции, таких как [пакета](../xmla/xml-elements-commands/batch-element-xmla.md) команду, при этом запрещать другие приложения из зафиксировать транзакцию записи в базу данных.  
  
## <a name="locking-databases"></a>Блокировка баз данных  
 Команда `Lock` блокирует объект для совместного или монопольного использования в контексте текущей активной транзакции. Блокировка объекта не позволяет фиксировать транзакции, пока она не будет снята. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает два типа блокировок: совмещаемые и монопольные блокировки. Дополнительные сведения о поддерживаемых типах блокировки [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], см. в разделе [элемент Mode &#40;XMLA&#41;](../xmla/xml-elements-properties/mode-element-xmla.md).  
  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] позволяют блокировать только базы данных. [Объект](../xmla/xml-elements-properties/object-element-xmla.md) элемент должен содержать ссылку на объект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. Если элемент `Object` не указан или если элемент `Object` ссылается на объект, отличающийся от базы данных, возникает ошибка.  
  
> [!IMPORTANT]  
>  Явно выполнять команду `Lock` могут только администраторы базы данных или администраторы сервера.  
  
 Другие команды неявно выполняют команду `Lock` для базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Любая операция, которая считывает данные или метаданные из базы данных, например любой [Discover](../xmla/xml-elements-methods-discover.md) метод или [Execute](../xmla/xml-elements-methods-execute.md) метод, выполняемый [инструкции](../xmla/xml-elements-commands/statement-element-xmla.md) команды, неявно устанавливает общих ресурсов блокировки в базе данных. Любая транзакция, фиксирующая изменения в данных или метаданных объекта в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных, такие как `Execute` метод, выполняемый [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) команды, неявно устанавливает монопольную блокировку базы данных.  
  
## <a name="unlocking-objects"></a>Снятие блокировки с объектов  
 Команда `Unlock` снимает блокировку, установленную в контексте транзакции, активной в настоящее время.  
  
> [!IMPORTANT]  
>  Только администраторы базы данных или администраторы сервера могут явно выдавать команду `Unlock`.  
  
 Все блокировки удерживаются в контексте текущей транзакции. После фиксации или отката текущей транзакции все блокировки, определенные в рамках транзакции, автоматически снимаются.  
  
## <a name="see-also"></a>См. также  
 [Заблокировать элемент &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/lock-element-xmla.md)   
 [Разблокировать элемент &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
