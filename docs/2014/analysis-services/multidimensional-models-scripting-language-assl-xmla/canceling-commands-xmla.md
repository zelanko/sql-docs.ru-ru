---
title: Отмена команд (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5129dd84cdd120b778fb55986374d27055b5904c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096276"
---
# <a name="canceling-commands-xmla"></a>Отмена команд (XMLA)
  В зависимости от того, какие административные разрешения пользователя, выполняющего команду [отменить](../xmla/xml-elements-commands/cancel-element-xmla.md) команды в формате XML для аналитики (XMLA) может отменить команду на сеанс, сеанс, соединение, серверный процесс или связанного с ним сеанса или соединение.  
  
## <a name="canceling-commands"></a>Отмена команд  
 Пользователь может отменить выполняемую в данный момент команду в контексте текущего явного сеанса, отправив команду `Cancel` без указания свойств.  
  
> [!NOTE]  
>  Пользователь не может отменить команду, выполняющуюся в рамках неявного сеанса.  
  
### <a name="canceling-batch-commands"></a>Отмена пакетов команд  
 Если пользователь отменяет команду `Batch`, то отменяются все остальные команды в рамках команды `Batch`, выполнение которых еще не завершено. Если команда `Batch` входила в состав транзакции, то происходит откат всех команд, которые выполнялись до запуска команды `Cancel`.  
  
## <a name="canceling-sessions"></a>Отмена сеансов  
 Указав идентификатор сеанса для явного сеанса в [SessionID](../xmla/xml-elements-properties/id-element-xmla.md) свойство `Cancel` команды, администратор базы данных или администратор сервера может отменить сеанс, включая выполняемую команду . Администратор баз данных может отменять сеансы только для тех баз данных, на которые у него есть разрешения администратора.  
  
 Администратор базы данных может извлекать сведения об активных сеансах для указанной базы данных путем извлечения набора строк схемы DISCOVER_SESSIONS. Для получения набора строк схемы DISCOVER_SESSIONS, администратор базы данных использует XML для Аналитики `Discover` метод и задает идентификатор соответствующей базы данных для столбца ограничений SESSION_CURRENT_DATABASE в [ограничения](../xmla/xml-elements-properties/restrictions-element-xmla.md) свойство `Discover` метод.  
  
## <a name="canceling-connections"></a>Отмена соединений  
 Указав идентификатор соединения в [ConnectionID](../xmla/xml-elements-properties/connectionid-element-xmla.md) свойство `Cancel` команды, администратор сервера может отменить все сеансы, ассоциированные с данным соединением, включая все выполняющиеся команды, и Отмените соединение.  
  
> [!NOTE]  
>  Если экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не удается обнаружить и отменить сеансы, ассоциированные с соединением, например, когда средство переноса данных открывает несколько сеансов, обеспечивая подключения по протоколу HTTP, экземпляр не может отменить соединение. Если такая ситуация возникает во время выполнения команды `Cancel`, возникает ошибка.  
  
 Администратор сервера может извлекать сведения об активных соединениях для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] путем извлечения набора строк схемы DISCOVER_CONNECTIONS при помощи метода XMLA `Discover`.  
  
## <a name="canceling-server-processes"></a>Отмена процессов сервера  
 Указав идентификатор процесса сервера (SPID) в [SPID](../xmla/xml-elements-properties/spid-element-xmla.md) свойство `Cancel` команды, администратор сервера могут отменять команды, связанные с данным идентификатором SPID.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Отмена ассоциированных сеансов и соединений  
 Можно задать [CancelAssociated](../xmla/xml-elements-properties/cancelassociated-element-xmla.md) значение true для отмены соединения, сеансы и команды, связанные с подключением, сеанса или идентификатором SPID, указанным в `Cancel` команды.  
  
## <a name="see-also"></a>См. также  
 [Метод Discover &#40;XML для Аналитики&#41;](../xmla/xml-elements-methods-discover.md)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  