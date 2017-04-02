---
title: "Редактор задачи &#171;Передача сообщений об ошибках&#187; (страница &#171;Сообщения&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transfererrormessagestask.errormessages.F1"
helpviewer_keywords: 
  - "редактор задачи «Передача сообщений об ошибках»"
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Редактор задачи &#171;Передача сообщений об ошибках&#187; (страница &#171;Сообщения&#187;)
  Используйте страницу **Сообщения** диалогового окна **Редактор задачи "Передача сообщений об ошибках"**, чтобы указать свойства копирования одного или более определенных пользователем сообщений об ошибках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в другой. Дополнительные сведения об этой задаче см. в разделе [Transfer Error Messages Task](../../integration-services/control-flow/transfer-error-messages-task.md).  
  
## Параметры  
 **SourceConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к целевому серверу.  
  
 **IfObjectExists**  
 Выберите, следует ли при выполнении задачи перезаписать существующие пользовательские сообщения об ошибках, оставить их без изменения или зарегистрировать сбой в случае, если сообщения об ошибках с тем же именем уже существуют на целевом сервере.  
  
 **TransferAllErrorMessages**  
 Выберите, следует ли при выполнении задачи копировать все или только указанные пользовательские сообщения с исходного сервера на целевой сервер.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**True**|Копировать все пользовательские сообщения.|  
|**False**|Копировать только указанные пользовательские сообщения.|  
  
 **ErrorMessagesList**  
 Нажмите кнопку обзора, обозначенную многоточием **(...)**, чтобы выбрать сообщения об ошибках для копирования.  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
 **ErrorMessageLanguagesList**  
 Нажмите кнопку обзора, обозначенную многоточием **(...)**, чтобы выбрать языки, для которых должны быть скопированы на целевой сервер пользовательские сообщения об ошибках. Прежде чем можно будет передать на целевой сервер версии сообщения на других языках, на нем должна существовать англоязычная версия сообщения (кодовая страница 1033, us_english).  
  
> [!NOTE]  
>  Необходимо указать значение параметра **SourceConnection** прежде, чем можно будет выбрать сообщения об ошибках для копирования.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача сообщений об ошибках" (страница "Общие")](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)   
 [Редактор задачи "Передача сообщений об ошибках" (страница "Общие")](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  