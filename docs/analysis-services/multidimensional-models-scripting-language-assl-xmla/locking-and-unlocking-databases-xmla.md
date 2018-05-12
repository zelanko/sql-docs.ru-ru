---
title: Блокировка и снятие блокировки баз данных (XMLA) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d9868b251ff95fae1822abb5844ff7e909940dae
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="locking-and-unlocking-databases-xmla"></a>Блокировка и снятие блокировки баз данных (XMLA)
  Блокировка и снятие блокировки баз данных с помощью, соответственно, [блокировки](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) и [Unlock](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) команды в XML для аналитики (XMLA). Другие команды XML для аналитики также при необходимости автоматически блокируют и снимают блокировку объектов в процессе выполнения команды. Вы явным образом заблокировать или разблокировать базу данных для выполнения нескольких команд в одной транзакции, таких как [пакета](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) команду, чтобы зафиксировать транзакцию записи в базу данных другие приложения не.  
  
## <a name="locking-databases"></a>Блокировка баз данных  
 Команда **Lock** блокирует объект для совместного или монопольного использования в контексте текущей активной транзакции. Блокировка объекта не позволяет фиксировать транзакции, пока она не будет снята. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает два типа блокировок: совмещаемые и монопольные блокировки. Дополнительные сведения о поддерживаемых типах блокировки [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], в разделе [режим элемент & #40; XML для Аналитики & #41; ](../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] позволяют блокировать только базы данных. [Объекта](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) элемент должен содержать ссылку на объект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. Если элемент **Object** не указан или если элемент **Object** ссылается на объект, отличающийся от базы данных, возникает ошибка.  
  
> [!IMPORTANT]  
>  Явно выполнять команду **Lock** могут только администраторы базы данных или администраторы сервера.  
  
 Другие команды неявно выполняют **блокировки** на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. Любая операция, которая считывает данных или метаданных из базы данных, например любой [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) метода или [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) метод, выполняемый [инструкции](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) неявным образом общий блокировки в базе данных. Любая транзакция, фиксирующая изменения в данных или метаданных объекта в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных, например **Execute** метод, выполняемый [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) неявным образом устанавливает монопольную блокировку на База данных.  
  
## <a name="unlocking-objects"></a>Снятие блокировки с объектов  
 Команда **Unlock** снимает блокировку, установленную в контексте транзакции, активной в настоящее время.  
  
> [!IMPORTANT]  
>  Только администраторы базы данных или администраторы сервера могут явно выдавать команду **Unlock** .  
  
 Все блокировки удерживаются в контексте текущей транзакции. После фиксации или отката текущей транзакции все блокировки, определенные в рамках транзакции, автоматически снимаются.  
  
## <a name="see-also"></a>См. также  
 [Заблокировать элемент &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Разблокировать элемент & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
