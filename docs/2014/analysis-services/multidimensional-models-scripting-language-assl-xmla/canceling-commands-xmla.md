---
title: Отмена команд (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba972db55dd5754bdd55c5c53caaaf45f8cc033f
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145009"
---
# <a name="canceling-commands-xmla"></a>Отмена команд (XMLA)
  В зависимости от прав администратора для пользователя, выполняющего команду [отменить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) команды XML для аналитики (XMLA) может отменить команду на сеанс, сеанс, подключение, серверный процесс или связанного с ним сеанса или подключение.  
  
## <a name="canceling-commands"></a>Отмена команд  
 Пользователь может отменить выполняемую в данный момент команду в контексте текущего явного сеанса, отправив команду `Cancel` без указания свойств.  
  
> [!NOTE]  
>  Пользователь не может отменить команду, выполняющуюся в рамках неявного сеанса.  
  
### <a name="canceling-batch-commands"></a>Отмена пакетов команд  
 Если пользователь отменяет команду `Batch`, то отменяются все остальные команды в рамках команды `Batch`, выполнение которых еще не завершено. Если команда `Batch` входила в состав транзакции, то происходит откат всех команд, которые выполнялись до запуска команды `Cancel`.  
  
## <a name="canceling-sessions"></a>Отмена сеансов  
 Указав идентификатор сеанса для явного сеанса в [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) свойство `Cancel` команды, администратор базы данных или администратор сервера может отменить сеанс, включая текущей выполняемой команды . Администратор баз данных может отменять сеансы только для тех баз данных, на которые у него есть разрешения администратора.  
  
 Администратор базы данных может извлекать сведения об активных сеансах для указанной базы данных путем извлечения набора строк схемы DISCOVER_SESSIONS. Чтобы получить набор строк схемы DISCOVER_SESSIONS, администратор базы данных использует XML для Аналитики `Discover` метод и задает идентификатор для ограничений session_current_database в соответствующей базе данных [ограничения](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) свойство `Discover` метод.  
  
## <a name="canceling-connections"></a>Отмена соединений  
 Указав идентификатор соединения в [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) свойство `Cancel` команды, администратор сервера может отменить все сеансы, ассоциированные с данным соединением, включая все выполняющиеся команды, и Отмените само соединение.  
  
> [!NOTE]  
>  Если экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не удается обнаружить и отменить сеансы, ассоциированные с соединением, например, когда средство переноса данных открывает несколько сеансов, обеспечивая подключения по протоколу HTTP, экземпляр не может отменить соединение. Если такая ситуация возникает во время выполнения команды `Cancel`, возникает ошибка.  
  
 Администратор сервера может извлекать сведения об активных соединениях для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] путем извлечения набора строк схемы DISCOVER_CONNECTIONS при помощи метода XMLA `Discover`.  
  
## <a name="canceling-server-processes"></a>Отмена процессов сервера  
 Указав идентификатор серверного процесса (SPID) в [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) свойство `Cancel` команды, администратор сервера может отменять команды, связанные с данным идентификатором SPID.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Отмена ассоциированных сеансов и соединений  
 Можно задать [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) присваивается значение true для отмены соединения, сеансы и команды, связанные с подключения, сеансом или идентификатором SPID, указанным в `Cancel` команды.  
  
## <a name="see-also"></a>См. также  
 [Метод Discover &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
