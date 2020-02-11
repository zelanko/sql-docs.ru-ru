---
title: Отмена команд (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 80bddac8f800c1b9394c1ed605007ab0f2137b88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727468"
---
# <a name="canceling-commands-xmla"></a>Отмена команд (XMLA)
  В зависимости от административных разрешений пользователя, выполняющего команду, команда [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) в XML для АНАЛИТИКИ (XMLA) может отменить команду в сеансе, сеансе, подключении, серверном процессе или связанном сеансе или соединении.  
  
## <a name="canceling-commands"></a>Отмена команд  
 Пользователь может отменить выполняемую в данный момент команду в контексте текущего явного сеанса, отправив команду `Cancel` без указания свойств.  
  
> [!NOTE]  
>  Пользователь не может отменить команду, выполняющуюся в рамках неявного сеанса.  
  
### <a name="canceling-batch-commands"></a>Отмена пакетов команд  
 Если пользователь отменяет команду `Batch`, то отменяются все остальные команды в рамках команды `Batch`, выполнение которых еще не завершено. Если команда `Batch` входила в состав транзакции, то происходит откат всех команд, которые выполнялись до запуска команды `Cancel`.  
  
## <a name="canceling-sessions"></a>Отмена сеансов  
 Указав идентификатор сеанса для явного сеанса в свойстве [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) `Cancel` команды, администратор базы данных или администратор сервера может отменить сеанс, включая выполняемую в данный момент команду. Администратор баз данных может отменять сеансы только для тех баз данных, на которые у него есть разрешения администратора.  
  
 Администратор базы данных может извлекать сведения об активных сеансах для указанной базы данных путем извлечения набора строк схемы DISCOVER_SESSIONS. Для получения набора строк схемы DISCOVER_SESSIONS администратор базы данных использует метод XMLA `Discover` и указывает соответствующий идентификатор базы данных для столбца ограничений SESSION_CURRENT_DATABASE в свойстве restriction [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) `Discover` метода.  
  
## <a name="canceling-connections"></a>Отмена соединений  
 Указав идентификатор соединения в свойстве [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) `Cancel` команды, администратор сервера может отменить все сеансы, связанные с данным подключением, включая все выполняющиеся команды, и отменить подключение.  
  
> [!NOTE]  
>  Если экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не может располагать и отменять сеансы, связанные с соединением, например, когда в конвейере данных открывается несколько сеансов и предоставляется возможность подключения по протоколу HTTP, экземпляр не может отменить подключение. Если такая ситуация возникает во время выполнения команды `Cancel`, возникает ошибка.  
  
 Администратор сервера может извлекать сведения об активных соединениях для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] путем извлечения набора строк схемы DISCOVER_CONNECTIONS при помощи метода XMLA `Discover`.  
  
## <a name="canceling-server-processes"></a>Отмена процессов сервера  
 Указав идентификатор серверного процесса (SPID) в свойстве [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) `Cancel` команды, администратор сервера может отменить команды, связанные с данным идентификатором SPID.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Отмена ассоциированных сеансов и соединений  
 Можно задать для свойства [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) значение true, чтобы отменить соединения, сеансы и команды, связанные с соединением, сеансом или SPID, указанными `Cancel` в команде.  
  
## <a name="see-also"></a>См. также:  
 [Метод Discover &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
