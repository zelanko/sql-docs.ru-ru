---
title: "Редактор задачи &#171;FTP&#187; (страница &#171;Передача файлов&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftptask.filetransfer.f1"
helpviewer_keywords: 
  - "редактор задачи FTP"
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Редактор задачи &#171;FTP&#187; (страница &#171;Передача файлов&#187;)
  Страница **Передача файлов** диалогового окна **Редактор задачи «FTP»** используется для настройки операции FTP, выполняемой задачей.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача FTP](../../integration-services/control-flow/ftp-task.md).  
  
## Параметры  
 **IsRemotePathVariable**  
 Укажите, хранится ли удаленный путь в переменной. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**True**|Целевой путь хранится в переменной. Выбор этого значения отображает динамический параметр **RemoteVariable**.|  
|**False**|Целевой путь задается в диспетчере подключения файлов. Выбор этого значения отображает динамический параметр **RemotePath**.|  
  
 **OverwriteFileAtDestination**  
 Задайте, можно ли заменять файл в месте назначения.  
  
 **IsLocalPathVariable**  
 Укажите, хранится ли локальный путь в переменной. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**True**|Целевой путь хранится в переменной. Выбор этого значения отображает динамический параметр **LocalVariable**.|  
|**False**|Целевой путь задается в диспетчере подключения файлов. Выбор этого значения отображает динамический параметр **LocalPath**.|  
  
 **Операция**  
 Выберите операцию протокола FTP для выполнения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Отправить файлы**|Отправляет файлы. При выборе этого значения выводятся динамические параметры **LocalVariable**, **LocalPathRemoteVariable** и **RemotePath**.|  
|**Получить файлы**|Получает файлы. При выборе этого значения выводятся динамические параметры **LocalVariable**, **LocalPathRemoteVariable** и **RemotePath**.|  
|**Создать локальный каталог**|Создает локальный каталог. При выборе этого значения выводятся динамические параметры **LocalVariable** и **LocalPath**.|  
|**Создать удаленный каталог**|Создает удаленный каталог. При выборе этого значения выводятся динамические параметры **RemoteVariable** и **RemoteIPath**.|  
|**Удалить локальный каталог**|Удаляет локальный каталог. При выборе этого значения выводятся динамические параметры **LocalVariable** и **LocalPath**.|  
|**Удалить удаленный каталог**|Удаляет удаленный каталог. При выборе этого значения выводятся динамические параметры **RemoteVariable** и **RemotePath**.|  
|**Удалить локальные файлы**|Удаляет локальные файлы. При выборе этого значения выводятся динамические параметры **LocalVariable** и **LocalPath**.|  
|**Удалить удаленные файлы**|Удаляет удаленные файлы. При выборе этого значения выводятся динамические параметры **RemoteVariable** и **RemotePath**.|  
  
 **IsTransferASCII**  
 Укажите, должны ли файлы, передаваемые на и с удаленного FTP-сервера, передаваться в режиме ASCII.  
  
## Динамические параметры IsRemotePathVariable  
  
### IsRemotePathVariable = True  
 **RemoteVariable**  
 Выберите существующую пользовательскую переменную или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), Добавление переменной  
  
### IsRemotePathVariable = False  
 **RemotePath**  
 Выберите существующий диспетчер подключений FTP или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [Диспетчер FTP-соединений](../../integration-services/connection-manager/ftp-connection-manager.md), [Редактор диспетчера FTP-сеансов](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
## Динамические параметры IsLocalPathVariable  
  
### IsLocalPathVariable = True  
 **LocalVariable**  
 Выберите существующую пользовательскую переменную или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), Добавление переменной  
  
### IsLocalPathVariable = False  
 **LocalPath**  
 Выберите существующий диспетчер подключений файлов или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также**: [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "FTP" (страница "Общие")](../../integration-services/control-flow/ftp-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
  