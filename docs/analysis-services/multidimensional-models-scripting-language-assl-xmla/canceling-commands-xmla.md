---
title: Отмена команд (XMLA) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 313708ad1575c7b9922ac796791d0d623c51b54b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63182940"
---
# <a name="canceling-commands-xmla"></a>Отмена команд (XMLA)
  В зависимости от прав администратора для пользователя, выполняющего команду [отменить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) команды XML для аналитики (XMLA) может отменить команду на сеанс, сеанс, подключение, серверный процесс или связанного с ним сеанса или подключение.  
  
## <a name="canceling-commands"></a>Отмена команд  
 Пользователь может отменить команду, выполняемую в контексте текущего явного сеанса, отправляя **отменить** команду без указания свойств.  
  
> [!NOTE]  
>  Пользователь не может отменить команду, выполняющуюся в рамках неявного сеанса.  
  
### <a name="canceling-batch-commands"></a>Отмена пакетов команд  
 Если пользователь отменяет **пакета** команда, а затем все остальные команды, которые еще не выполнена в **пакета** команды будут отменены. Если **пакета** входила в состав команды, всех команд, которые выполнялись до **отменить** откат выполняется команда.  
  
## <a name="canceling-sessions"></a>Отмена сеансов  
 Указав идентификатор сеанса для явного сеанса в [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) свойство **отменить** команды, администратор базы данных или администратор сервера может отменить сеанс, в том числе текущей исполняемой команды. Администратор баз данных может отменять сеансы только для тех баз данных, на которые у него есть разрешения администратора.  
  
 Администратор базы данных может извлекать сведения об активных сеансах для указанной базы данных путем извлечения набора строк схемы DISCOVER_SESSIONS. Чтобы получить набор строк схемы DISCOVER_SESSIONS, администратор базы данных использует XML для Аналитики **Discover** метод и задает идентификатор соответствующей базе данных для ограничений session_current_database в [Ограничения](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) свойство **Discover** метод.  
  
## <a name="canceling-connections"></a>Отмена соединений  
 Указав идентификатор соединения в [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) свойство **отменить** команды, администратор сервера может отменить все сеансы, ассоциированные с данным соединением, включая все Выполнение команд и отменить само соединение.  
  
> [!NOTE]
>  Если экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не удается обнаружить и отменить сеансы, ассоциированные с соединением, например, когда средство переноса данных открывает несколько сеансов, обеспечивая подключения по протоколу HTTP, экземпляр не может отменить соединение. Если такая ситуация возникает во время выполнения **отменить** команды произошла ошибка.  
  
 Администратор сервера может извлекать активных подключений для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра путем извлечения набора строк схемы DISCOVER_CONNECTIONS, с помощью XML для Аналитики **Discover** метод.  
  
## <a name="canceling-server-processes"></a>Отмена процессов сервера  
 Указав идентификатор серверного процесса (SPID) в [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) свойство **отменить** команды, администратор сервера может отменять команды, связанные с данным идентификатором SPID.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Отмена ассоциированных сеансов и соединений  
 Можно задать [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) присваивается значение true для отмены соединения, сеансы и команды, связанные с подключения, сеансом или идентификатором SPID, указанным в **отменить** команды.  
  
## <a name="see-also"></a>См. также  
 [Метод Discover &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
