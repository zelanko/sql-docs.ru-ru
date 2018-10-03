---
title: Редактор задачи «FTP» (страница «Передача файла») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9fff9948011cd81df80e71237d8381079e52bbf6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087484"
---
# <a name="ftp-task-editor-file-transfer-page"></a>Редактор задачи «FTP» (страница «Передача файлов»)
  Страница **Передача файлов** диалогового окна **Редактор задачи «FTP»** используется для настройки операции FTP, выполняемой задачей.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача FTP](control-flow/ftp-task.md).  
  
## <a name="options"></a>Параметры  
 **IsRemotePathVariable**  
 Укажите, хранится ли удаленный путь в переменной. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Целевой путь хранится в переменной. Выбор этого значения отображает динамический параметр **RemoteVariable**.|  
|**False**|Целевой путь задается в диспетчере подключения файлов. Выбор этого значения отображает динамический параметр **RemotePath**.|  
  
 **OverwriteFileAtDestination**  
 Задайте, можно ли заменять файл в месте назначения.  
  
 **IsLocalPathVariable**  
 Укажите, хранится ли локальный путь в переменной. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Целевой путь хранится в переменной. Выбор этого значения отображает динамический параметр **LocalVariable**.|  
|**False**|Целевой путь задается в диспетчере подключения файлов. Выбор этого значения отображает динамический параметр **LocalPath**.|  
  
 **Операция**  
 Выберите операцию протокола FTP для выполнения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
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
 Выберите существующую пользовательскую переменную или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md), Добавление переменной  
  
### <a name="isremotepathvariable--false"></a>IsRemotePathVariable = False  
 **RemotePath**  
 Выберите существующий диспетчер подключений FTP или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [Диспетчер FTP-соединений](connection-manager/ftp-connection-manager.md), [Редактор диспетчера FTP-сеансов](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
## <a name="islocalpathvariable-dynamic-options"></a>Динамические параметры IsLocalPathVariable  
  
### <a name="islocalpathvariable--true"></a>IsLocalPathVariable = True  
 **LocalVariable**  
 Выберите существующую пользовательскую переменную или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md), Добавление переменной  
  
### <a name="islocalpathvariable--false"></a>IsLocalPathVariable = False  
 **LocalPath**  
 Выберите существующий диспетчер подключений файлов или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также**: [Flat File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи «FTP» &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница "Выражения"](expressions/expressions-page.md)  
  
  
