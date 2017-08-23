---
title: "Средства устранения неполадок соединения пакетов | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e3799e224930806445bc1c27f37c05b95a0bbbae
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="troubleshooting-tools-for-package-connectivity"></a>Инструменты устранения неполадок с соединением пакетов
Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают в себя функции и средства, которые используются для устранения неполадок соединений между пакетами и источниками данных, из которых пакеты извлекают и загружают данные.  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a>Устранение неполадок, связанных с внешними поставщиками данных  
 Многие ошибки в работе пакетов возникают при взаимодействии с внешними поставщиками данных. Однако сообщения, которые возвращают эти поставщики в службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , часто не предоставляют достаточных сведений для устранения неполадок. В ответ на требования, связанные с устранением неисправностей, в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] были добавлены новые сообщения ведения журналов, которые можно использовать для устранения неполадок взаимодействия пакета с внешними источниками данных.  
  
-   **Чтобы просматривать сообщения, связанные с устранением неисправностей, необходимо разрешить запись в журнал и выбрать событие пакета «Диагностика».** Следующие компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обеспечивают возможность записи сообщений в журнал перед каждым обращением к внешнему поставщику данных и после этого.  
  
    -   Диспетчер соединений OLE DB, источник OLE DB и назначение «OLE DB»  
  
    -   [!INCLUDE[vstecado](../../includes/vstecado-md.md)]Диспетчер соединений и источник ADO NET  
  
    -   Задача «Выполнение SQL»  
  
    -   Преобразование «Уточняющий запрос», преобразование «Команда OLE DB» и преобразование «Медленно изменяющееся измерение»  
  
     Сообщения журнала содержат название вызываемого метода. Например, эти сообщения журнала могут содержать метод **Open** объекта OLE DB **Connection** или метод **ExecuteNonQuery** объекта **Command** . Сообщения имеют следующий формат, где "%1!s!" — заполнитель для сведений метода:  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     Для устранения неполадок взаимодействия с внешним поставщиком данных просмотрите журнал, чтобы убедиться, что каждое входящее сообщение (`ExternalRequest_pre`) имеет соответствующее подтверждающее сообщение (`ExternalRequest_post`). Если соответствующее подтверждающее сообщение отсутствует, то это означает, что внешний поставщик данных не ответил так, как это ожидалось.  
  
     В следующем примере показаны несколько образцов строк из журнала, содержащего эти сообщения.  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Инструменты устранения неполадок при разработке пакета](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Средства устранения неполадок при выполнении пакета](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
