---
title: "Редактор задачи &#171;Передача главных хранимых процедур&#187; (страница &#171;Хранимые процедуры&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.transferstoredprocedurestask.storedprocedures.f1"
helpviewer_keywords: 
  - "редактор задачи «Передача хранимых процедур»"
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 20
---
# Редактор задачи &#171;Передача главных хранимых процедур&#187; (страница &#171;Хранимые процедуры&#187;)
  На странице **Хранимые процедуры** диалогового окна **Редактор задачи "Передача главных хранимых процедур"** укажите свойства для копирования одной или нескольких пользовательских хранимых процедур из базы данных **master** одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базу данных **master** другого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об этой задаче см. в разделе [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Эта задача передает только пользовательские хранимые процедуры, принадлежащие **dbo**, из базы данных **master** на исходном сервере в базу данных **master** на целевом сервере. Пользователям должно быть предоставлено разрешение CREATE PROCEDURE в базе данных **master** на целевом сервере, или они должны быть членами предопределенной роли сервера **sysadmin** на целевом сервере, чтобы создавать на нем хранимые процедуры.  
  
## Параметры  
 **SourceConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к целевому серверу.  
  
 **IfObjectExists**  
 Выберите, каким способом задача будет обрабатывать пользовательские хранимые процедуры с именами, уже существующими в базе данных **master** на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**FailTask**|Если в базе данных **master** на целевом сервере уже существуют хранимые процедуры с теми же именами, задача завершается ошибкой.|  
|**Overwrite**|Задача перезаписывает хранимые процедуры с теми же именами в базе данных **master** на целевом сервере.|  
|**Skip**|Задача пропускает хранимые процедуры с теми же именами в базе данных **master** на целевом сервере.|  
  
 **TransferAllStoredProcedures**  
 Укажите, все ли пользовательские хранимые процедуры в базе данных **master** на исходном сервере следует копировать на целевой сервер.  
  
|Значение|Description|  
|-----------|-----------------|  
|**True**|Копировать все пользовательские хранимые процедуры базы данных **master**.|  
|**False**|Копировать только указанные хранимые процедуры.|  
  
 **StoredProceduresList**  
 Укажите, какие пользовательские хранимые процедуры в базе данных **master** на исходном сервере следует копировать в целевую базу данных **master**. Этот параметр доступен, только если параметру **TransferAllStoredProcedures** присвоено значение **False**.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача главных хранимых процедур" (страница "Общие")](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  