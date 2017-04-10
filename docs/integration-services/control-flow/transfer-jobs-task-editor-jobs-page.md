---
title: "Редактор задачи &#171;Передача заданий&#187; (страница &#171;Задания&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.transferjobstask.jobs.f1"
helpviewer_keywords: 
  - "редактор задачи «Передача заданий»"
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Редактор задачи &#171;Передача заданий&#187; (страница &#171;Задания&#187;)
  Используйте страницу **Задания** диалогового окна **Редактор задачи «Передача заданий»** для определения свойств копирования одного или более заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в другой. Дополнительные сведения о задаче «Передача заданий» см. в разделе [Transfer Jobs Task](../../integration-services/control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Для доступа к задачам на исходном сервере пользователи должны быть членами хотя бы одной предопределенной роли базы данных **SQLAgentUserRole** на этом сервере. Для успешного создания задания на целевом сервере пользователь должен быть членом предопределенной роли сервера **sysadmin** или одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их разрешениях см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## Параметры  
 **SourceConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к целевому серверу.  
  
 **TransferAllJobs**  
 Укажите, должна задача копировать с исходного сервера на целевой все задания или только те, которые указаны агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**True**|Копировать все задания.|  
|**False**|Копировать только выбранные задания.|  
  
 **JobsList**  
 Нажмите кнопку обзора **(…)**, чтобы выбрать задания для копирования. Необходимо выбрать хотя бы одно задание.  
  
> [!NOTE]  
>  Прежде чем выбирать задания для копирования, укажите свойство **SourceConnection**.  
  
 Параметр **JobsList** недоступен, если параметр **TransferAllJobs** равен **True**.  
  
 **IfObjectExists**  
 Определите, как задача должна обрабатывать задания с именем, которое уже есть на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**FailTask**|Задача завершается сбоем, если задание с таким именем уже есть на целевом сервере.|  
|**Overwrite**|Задача перезаписывает задание с таким же именем на целевом сервере.|  
|**Skip**|Задача пропускает задание, если задание с таким именем уже есть на целевом сервере.|  
  
 **EnableJobsAtDestination**  
 Определите, будут ли активированы задания, скопированные на целевой сервер.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**True**|Включить задания на целевом сервере.|  
|**False**|Отключить задания на целевом сервере.|  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача заданий" (страница "Общие")](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  