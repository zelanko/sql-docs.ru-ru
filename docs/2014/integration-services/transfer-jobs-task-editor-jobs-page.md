---
title: Редактор задачи задания (страница «задания») передача | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
caps.latest.revision: 22
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 119e9c7828e9ba794e13b484bf0b204e237a6aa1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37184781"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a>Редактор задачи «Передача заданий» (страница «Задания»)
  Используйте страницу **Задания** диалогового окна **Редактор задачи «Передача заданий»** для определения свойств копирования одного или более заданий агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в другой. Дополнительные сведения о задаче «Передача заданий» см. в разделе [Transfer Jobs Task](control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Для доступа к задачам на исходном сервере пользователи должны быть членами хотя бы одной предопределенной роли базы данных **SQLAgentUserRole** на этом сервере. Для успешного создания задания на целевом сервере пользователь должен быть членом предопределенной роли сервера **sysadmin** или одной из предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Дополнительные сведения о предопределенных ролях базы данных агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и их разрешениях см. в разделе [Предопределенные роли базы данных агента SQL Server](../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="options"></a>Параметры  
 **SourceConnection**  
 Выберите в списке диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать подключение к исходному серверу.  
  
 **DestinationConnection**  
 Выберите в списке диспетчер подключений SMO или нажмите кнопку **\<Создать подключение...>**, чтобы создать подключение к целевому серверу.  
  
 **TransferAllJobs**  
 Укажите, должна задача копировать с исходного сервера на целевой все задания или только те, которые указаны агентом [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Копировать все задания.|  
|**False**|Копировать только выбранные задания.|  
  
 **JobsList**  
 Нажмите кнопку обзора **(…)** , чтобы выбрать задания для копирования. Необходимо выбрать хотя бы одно задание.  
  
> [!NOTE]  
>  Прежде чем выбирать задания для копирования, укажите свойство **SourceConnection** .  
  
 Параметр **JobsList** недоступен, если параметр **TransferAllJobs** равен **True**.  
  
 **IfObjectExists**  
 Определите, как задача должна обрабатывать задания с именем, которое уже есть на целевом сервере.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**FailTask**|Задача завершается сбоем, если задание с таким именем уже есть на целевом сервере.|  
|**Overwrite**|Задача перезаписывает задание с таким же именем на целевом сервере.|  
|**Skip**|Задача пропускает задание, если задание с таким именем уже есть на целевом сервере.|  
  
 **EnableJobsAtDestination**  
 Определите, будут ли активированы задания, скопированные на целевой сервер.  
  
 Параметры этого свойства приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Включить задания на целевом сервере.|  
|**False**|Отключить задания на целевом сервере.|  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача заданий" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Страница «выражения»](expressions/expressions-page.md)   
 [Диспетчер подключений управляющих объектов SQL Server](connection-manager/smo-connection-manager.md)  
  
  
