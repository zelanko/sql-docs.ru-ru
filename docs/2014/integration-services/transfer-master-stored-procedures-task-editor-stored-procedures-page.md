---
title: Редактор задачи «перенос главных хранимых процедур» (страница «хранимые процедуры») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f233f0730286a1623ee54c38084d07a2aba903e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054863"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>Редактор задачи «Передача главных хранимых процедур» (страница «Хранимые процедуры»)
  На странице **Хранимые процедуры** диалогового окна **Редактор задачи "Передача главных хранимых процедур"** укажите свойства для копирования одной или нескольких пользовательских хранимых процедур из базы данных **master** одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в базу данных **master** другого экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения об этой задаче см. в разделе [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Эта задача передает только пользовательские хранимые процедуры, принадлежащие **dbo** , из базы данных **master** на исходном сервере в базу данных **master** на целевом сервере. Пользователям должно быть предоставлено разрешение CREATE PROCEDURE в базе данных **master** на целевом сервере, или они должны быть членами предопределенной роли сервера **sysadmin** на целевом сервере, чтобы создавать на нем хранимые процедуры.  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите в списке Диспетчер соединений SMO или нажмите кнопку ** \<создать соединение... >** , чтобы создать новое соединение с исходным сервером.  
  
 **DestinationConnection**  
 Выберите в списке Диспетчер соединений SMO или нажмите кнопку ** \<создать соединение... >** , чтобы создать новое соединение с целевым сервером.  
  
 **IfObjectExists**  
 Выберите, каким способом задача будет обрабатывать пользовательские хранимые процедуры с именами, уже существующими в базе данных **master** на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**FailTask**|Если в базе данных **master** на целевом сервере уже существуют хранимые процедуры с теми же именами, задача завершается ошибкой.|  
|**Перезаписать**|Задача перезаписывает хранимые процедуры с теми же именами в базе данных **master** на целевом сервере.|  
|**Сразу**|Задача пропускает хранимые процедуры с теми же именами в базе данных **master** на целевом сервере.|  
  
 **TransferAllStoredProcedures**  
 Укажите, все ли пользовательские хранимые процедуры в базе данных **master** на исходном сервере следует копировать на целевой сервер.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Условия**|Копировать все пользовательские хранимые процедуры базы данных **master** .|  
|**IsFalse**|Копировать только указанные хранимые процедуры.|  
  
 **StoredProceduresList**  
 Укажите, какие пользовательские хранимые процедуры в базе данных **master** на исходном сервере следует копировать в целевую базу данных **master** . Этот параметр доступен, только если параметру **TransferAllStoredProcedures** присвоено значение **False**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "перенос главных хранимых процедур" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [SMO, диспетчер соединений](connection-manager/smo-connection-manager.md)  
  
  
