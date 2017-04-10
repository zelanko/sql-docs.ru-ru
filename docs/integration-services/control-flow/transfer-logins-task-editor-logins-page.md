---
title: "Редактор задачи &#171;Передача имен входа&#187; (страница &#171;Имена входа&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.transferloginstask.logins.f1"
helpviewer_keywords: 
  - "редактор задачи «Передача имен входа»"
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Редактор задачи &#171;Передача имен входа&#187; (страница &#171;Имена входа&#187;)
  Страница **Имена входа** диалогового окна **Редактор задачи «Передача имен входа»** используется для задания свойств для копирования одного или более имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в другой. Дополнительные сведения об этой задаче см. в разделе [Transfer Logins Task](../../integration-services/control-flow/transfer-logins-task.md).  
  
> [!IMPORTANT]  
>  При выполнении задачи «Передача имен входа» имена создаются на целевом сервере со случайными паролями, и эти пароли отключаются. Для использования этих имен входа элемент предопределенной роли сервера **sysadmin** должен изменить пароли и затем включить их. Имя входа **sa** передать нельзя.  
  
## Параметры  
 **SourceConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите из списка диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать новое подключение к целевому серверу.  
  
 **LoginsToTransfer**  
 Выберите имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для копирования их с исходного сервера на целевой. Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**AllLogins**|Все имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на исходном сервере будут скопированы на целевой сервер.|  
|**SelectedLogins**|На целевой сервер будут скопированы только имена входа, заданные списком **LoginsList** .|  
|**AllLoginsFromSelectedDatabases**|Все имена входа из баз данных, заданных списком **DatabasesList** , будут скопированы на целевой сервер.|  
  
 **LoginsList**  
 Определяет имена входа на исходном сервере для копирования на целевой сервер. Этот параметр доступен только в том случае, если значение **SelectedLogins** выбрано для **LoginsToTransfer**.  
  
 **DatabasesList**  
 Определяет базы данных на исходном сервере, которые содержат имена входа для копирования на целевой сервер. Этот параметр доступен только в том случае, если значение **AllLoginsFromSelectedDatabases** выбрано для **LoginsToTransfer**.  
  
 **IfObjectExists**  
 Определяет то, как задача должна обрабатывать имена входа с тем же названием, что и у существующих на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**FailTask**|Задача не выполняется, если такое же имя входа уже существует на целевом сервере.|  
|**Overwrite**|Задача перезаписывает имя входа на целевом сервере.|  
|**Skip**|Задача пропускает обработку имени входа, если такое же имя входа уже существует на целевом сервере.|  
  
 **CopySids**  
 Определяет, будут ли скопированы на целевой сервер идентификаторы безопасности, связанные с именами входа. Параметр**CopySids** должен иметь значение **True** , если задача «Передача имен входа» используется вместе с задачей «Передача базы данных». В противном случае скопированные имена входа не будут распознаны переданными базами данных.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача имен входа" (страница "Общие")](../../integration-services/control-flow/transfer-logins-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)   
 [Надежные пароли](../../relational-databases/security/strong-passwords.md)   
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  