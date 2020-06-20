---
title: Средства устранения неполадок при подключении к пакету | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2dbeca0a1f49484061c894b33b9022a63cede712
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972686"
---
# <a name="troubleshooting-tools-package-connectivity"></a>Инструменты устранения неполадок соединения пакетов
  Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают в себя функции и средства, которые используются для устранения неполадок соединений между пакетами и источниками данных, из которых пакеты извлекают и загружают данные.  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a>Устранение неполадок, связанных с внешними поставщиками данных  
 Многие ошибки в работе пакетов возникают при взаимодействии с внешними поставщиками данных. Однако сообщения, которые возвращают эти поставщики в службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , часто не предоставляют достаточных сведений для устранения неполадок. В ответ на требования, связанные с устранением неисправностей, в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] были добавлены новые сообщения ведения журналов, которые можно использовать для устранения неполадок взаимодействия пакета с внешними источниками данных.  
  
-   **Чтобы просматривать сообщения, связанные с устранением неисправностей, необходимо разрешить запись в журнал и выбрать событие пакета «Диагностика».** Следующие компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обеспечивают возможность записи сообщений в журнал перед каждым обращением к внешнему поставщику данных и после этого.  
  
    -   Диспетчер соединений OLE DB, источник OLE DB и назначение «OLE DB»  
  
    -   Диспетчер подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] и источник ADO NET  
  
    -   Задача «Выполнение SQL»  
  
    -   Преобразование «Уточняющий запрос», преобразование «Команда OLE DB» и преобразование «Медленно изменяющееся измерение»  
  
     Сообщения журнала содержат название вызываемого метода. Например, эти сообщения журнала могут содержать метод `Open` объекта OLE DB `Connection` или метод `ExecuteNonQuery` объекта `Command`. Сообщения имеют следующий формат, где "%1!s!" — заполнитель для сведений метода:  
  
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
 [Инструменты устранения неполадок при разработке пакета](troubleshooting-tools-for-package-development.md)   
 [Устранение неполадок инструментов с помощью отчетов](troubleshooting-tools-for-package-execution.md)  
  
  
