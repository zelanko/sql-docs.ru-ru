---
title: Блокировка и разблокировка баз данных (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544996"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Блокировка и снятие блокировки баз данных (XMLA)
  Вы можете блокировать и разблокирование баз данных с помощью, соответственно, команд [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) и [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) в XML для аналитики (XMLA). Другие команды XML для аналитики также при необходимости автоматически блокируют и снимают блокировку объектов в процессе выполнения команды. Можно явно заблокировать или разблокировать базу данных для выполнения нескольких команд в одной транзакции, например [пакетной](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) командой, и предотвратить фиксацию транзакции записи в базе данных другими приложениями.  
  
## <a name="locking-databases"></a>Блокировка баз данных  
 Команда `Lock` блокирует объект для совместного или монопольного использования в контексте текущей активной транзакции. Блокировка объекта не позволяет фиксировать транзакции, пока она не будет снята. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает два типа блокировок: совмещаемые и монопольные блокировки. Дополнительные сведения о типах блокировок [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , поддерживаемых, см. в статье [элемент Mode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).  
  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] позволяют блокировать только базы данных. Команда [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) должен содержать ссылку на базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Если элемент `Object` не указан или если элемент `Object` ссылается на объект, отличающийся от базы данных, возникает ошибка.  
  
> [!IMPORTANT]  
>  Явно выполнять команду `Lock` могут только администраторы базы данных или администраторы сервера.  
  
 Другие команды неявно выполняют команду `Lock` для базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Любая операция по чтению данных или метаданных из базы данных, например любой метод [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) или метод [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) , запускающий команду [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) , неявно устанавливает совмещаемую блокировку для базы данных. Любая транзакция, которая фиксирует изменения в данных или метаданных для объекта в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базе данных, например `Execute` метод, выполняющий команду [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) , неявно выдает монопольную блокировку базы данных.  
  
## <a name="unlocking-objects"></a>Снятие блокировки с объектов  
 Команда `Unlock` снимает блокировку, установленную в контексте транзакции, активной в настоящее время.  
  
> [!IMPORTANT]  
>  Только администраторы базы данных или администраторы сервера могут явно выдавать команду `Unlock`.  
  
 Все блокировки удерживаются в контексте текущей транзакции. После фиксации или отката текущей транзакции все блокировки, определенные в рамках транзакции, автоматически снимаются.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Lock &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Разблокировка элемента &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
