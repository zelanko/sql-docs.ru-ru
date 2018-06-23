---
title: Редактор Передача главных хранимых процедур задачи (страница «хранимые процедуры») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2ee8337cfdf090e77c9161600a44d8d6d58d04f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194300"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>Редактор задачи «Передача главных хранимых процедур» (страница «Хранимые процедуры»)
  На странице **Хранимые процедуры** диалогового окна **Редактор задачи "Передача главных хранимых процедур"** укажите свойства для копирования одной или нескольких пользовательских хранимых процедур из базы данных **master** одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в базу данных **master** другого экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения об этой задаче см. в разделе [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Эта задача передает только пользовательские хранимые процедуры, принадлежащие **dbo** , из базы данных **master** на исходном сервере в базу данных **master** на целевом сервере. Пользователям должно быть предоставлено разрешение CREATE PROCEDURE в базе данных **master** на целевом сервере, или они должны быть членами предопределенной роли сервера **sysadmin** на целевом сервере, чтобы создавать на нем хранимые процедуры.  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите в списке диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите в списке диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать подключение к целевому серверу.  
  
 **IfObjectExists**  
 Выберите, каким способом задача будет обрабатывать пользовательские хранимые процедуры с именами, уже существующими в базе данных **master** на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**FailTask**|Если в базе данных **master** на целевом сервере уже существуют хранимые процедуры с теми же именами, задача завершается ошибкой.|  
|**Overwrite**|Задача перезаписывает хранимые процедуры с теми же именами в базе данных **master** на целевом сервере.|  
|**Skip**|Задача пропускает хранимые процедуры с теми же именами в базе данных **master** на целевом сервере.|  
  
 **TransferAllStoredProcedures**  
 Укажите, все ли пользовательские хранимые процедуры в базе данных **master** на исходном сервере следует копировать на целевой сервер.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Копировать все пользовательские хранимые процедуры базы данных **master** .|  
|**False**|Копировать только указанные хранимые процедуры.|  
  
 **StoredProceduresList**  
 Укажите, какие пользовательские хранимые процедуры в базе данных **master** на исходном сервере следует копировать в целевую базу данных **master** . Этот параметр доступен, только если параметру **TransferAllStoredProcedures** присвоено значение **False**.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор Передача главных хранимых процедур задач &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница «выражения»](expressions/expressions-page.md)   
 [Диспетчер подключений управляющих объектов SQL Server](connection-manager/smo-connection-manager.md)  
  
  