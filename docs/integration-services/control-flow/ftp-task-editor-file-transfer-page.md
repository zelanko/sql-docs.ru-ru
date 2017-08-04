---
title: "Редактор задачи «FTP» (страница «Передача файла») | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ca75f79962fcf7b7cae067a7d841f80f9c4c2032
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="ftp-task-editor-file-transfer-page"></a>Редактор задачи «FTP» (страница «Передача файлов»)
  Страница **Передача файлов** диалогового окна **Редактор задачи «FTP»** используется для настройки операции FTP, выполняемой задачей.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача FTP](../../integration-services/control-flow/ftp-task.md).  
  
## <a name="options"></a>Параметры  
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
  
## <a name="isremotepathvariable-dynamic-options"></a>Динамические параметры IsRemotePathVariable  
  
### <a name="isremotepathvariable--true"></a>IsRemotePathVariable = True  
 **RemoteVariable**  
 Выберите существующую переменную определяемых пользователем, или нажмите кнопку \< **создать переменную...** > для создания пользовательской переменной.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), Добавление переменной  
  
### <a name="isremotepathvariable--false"></a>IsRemotePathVariable = False  
 **RemotePath**  
 Выберите существующий диспетчер подключений FTP или щелкните \< **новое подключение...** > для создания диспетчера соединений.  
  
 **См. также:** [Диспетчер FTP-соединений](../../integration-services/connection-manager/ftp-connection-manager.md), [Редактор диспетчера FTP-сеансов](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
## <a name="islocalpathvariable-dynamic-options"></a>Динамические параметры IsLocalPathVariable  
  
### <a name="islocalpathvariable--true"></a>IsLocalPathVariable = True  
 **LocalVariable**  
 Выберите существующую переменную определяемых пользователем, или нажмите кнопку \< **создать переменную...** > для создания переменной.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), Добавление переменной  
  
### <a name="islocalpathvariable--false"></a>IsLocalPathVariable = False  
 **LocalPath**  
 Выберите существующий диспетчер подключения файлов или нажмите кнопку \< **новое подключение...** > для создания диспетчера соединений.  
  
 **См. также**: [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи «FTP» &#40; Страница "Общие" &#41;](../../integration-services/control-flow/ftp-task-editor-general-page.md)   
 [Страница "Выражения"](../../integration-services/expressions/expressions-page.md)  
  
  
