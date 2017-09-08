---
title: "Отмена команд (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e74ce7bd5b03aa84b6c6580342504148a62a68bf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="canceling-commands-xmla"></a>Отмена команд (XMLA)
  В зависимости от того, какие административные разрешения пользователя, выполняющего команду [отменить](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) команды в формате XML для аналитики (XMLA) может отменить команду на сеанс, сеанс, соединение, серверный процесс или связанного с ним сеанса или соединение.  
  
## <a name="canceling-commands"></a>Отмена команд  
 Пользователь может отменить команду, выполняемую в контексте текущего явного сеанса, отправив **отменить** команду без указания свойств.  
  
> [!NOTE]  
>  Пользователь не может отменить команду, выполняющуюся в рамках неявного сеанса.  
  
### <a name="canceling-batch-commands"></a>Отмена пакетов команд  
 Если пользователь отменяет **пакета** команду, а затем все остальные команды, еще не завершено в течение **пакета** команды будут отменены. Если **пакета** входила в состав транзакции, любые команды, которые выполнялись до **отменить** откат выполняется команда.  
  
## <a name="canceling-sessions"></a>Отмена сеансов  
 Указав идентификатор сеанса для явного сеанса в [SessionID](../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md) свойство **отменить** команды, администратор базы данных или администратор сервера может отменить сеанс, в том числе в настоящее время выполнения команды. Администратор баз данных может отменять сеансы только для тех баз данных, на которые у него есть разрешения администратора.  
  
 Администратор базы данных может извлекать сведения об активных сеансах для указанной базы данных путем извлечения набора строк схемы DISCOVER_SESSIONS. Для получения набора строк схемы DISCOVER_SESSIONS, администратор базы данных использует XML для Аналитики **Discover** метод и указывает соответствующий идентификатор базы данных для столбца ограничений SESSION_CURRENT_DATABASE в [Ограничения](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md) свойство **Discover** метод.  
  
## <a name="canceling-connections"></a>Отмена соединений  
 Указав идентификатор соединения в [ConnectionID](../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md) свойство **отменить** команды, администратор сервера может отменить все сеансы, ассоциированные с данным соединением, включая все Выполнение команд и отменить соединение.  
  
> [!NOTE]  
>  Если экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не удается обнаружить и отменить сеансы, ассоциированные с соединением, например, когда средство переноса данных открывает несколько сеансов, обеспечивая подключения по протоколу HTTP, экземпляр не может отменить соединение. Если такая ситуация возникает во время выполнения **отменить** команды, возникает ошибка.  
  
 Администратор сервера может получать активных соединений для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра путем извлечения набора строк схемы DISCOVER_CONNECTIONS, с помощью XML для Аналитики **Discover** метод.  
  
## <a name="canceling-server-processes"></a>Отмена процессов сервера  
 Указав идентификатор процесса сервера (SPID) в [SPID](../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md) свойство **отменить** команды, администратор сервера могут отменять команды, связанные с данным идентификатором SPID.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Отмена ассоциированных сеансов и соединений  
 Можно задать [CancelAssociated](../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md) значение true для отмены соединения, сеансы и команды, связанные с подключением, сеанса или идентификатором SPID, указанным в **отменить** команды.  
  
## <a name="see-also"></a>См. также:  
 [Обнаружение метод &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
