---
title: dbo.sysjobsteps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a9264ed33ffeea224f69b8a880e235753ead1467
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470749"
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения для каждого этапа задания, исполняемого агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**step_id**|**int**|Идентификатор этапа в задании.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**подсистемы**|**nvarchar(40)**|Имя подсистемы, используемой агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения шага задания.|  
|**команда**|**nvarchar(max)**|Команда, выполняемая по **подсистемы**.|  
|**flags**|**int**|Зарезервировано.|  
|**additional_parameters**|**ntext**|Зарезервировано.|  
|**cmdexec_success_code**|**int**|Значение уровня ошибки, возвращенный **CmdExec** шагами подсистемы в случае успеха.|  
|**on_success_action**|**tinyint**|Действие, выполняемое в случае успешного завершения шага.|  
|**on_success_step_id**|**int**|Идентификатор следующего этапа, выполняемого в случае успешного завершения шага.|  
|**on_fail_action**|**tinyint**|Действие, выполняемое в случае неуспешного завершения шага.|  
|**on_fail_step_id**|**int**|Идентификатор следующего этапа, выполняемого в случае неуспешного завершения шага.|  
|**server**|**sysname**|Зарезервировано.|  
|**database_name**|**sysname**|Имя базы данных, в котором **команда** выполняется, если **подсистемы** является TSQL.|  
|**database_user_name**|**sysname**|Имя пользователя базы данных, чья учетная запись будет использоваться для выполнения шага.|  
|**retry_attempts**|**int**|Число попыток повтора при неуспешном завершении шага.|  
|**retry_interval**|**int**|Время ожидания между попытками повтора.|  
|**os_run_priority**|**int**|Зарезервировано.|  
|**output_file_name**|**nvarchar(200)**|Имя файла, в котором выходные данные этапа, сохраняется **подсистемы** является TSQL, PowerShell, или **CmdExec**_._|  
|**last_run_outcome**|**int**|Результат предыдущего выполнения шага задания.<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **2** = повторение<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_run_duration**|**int**|Продолжительность (ччммсс) шага в секундах при последнем запуске.|  
|**last_run_retries**|**int**|Число попыток повтора в ходе последнего выполнения шага задания.|  
|**last_run_date**|**int**|Дата начала (ггггммдд) последнего выполнения шага.|  
|**last_run_time**|**int**|Время начала (ччммсс) последнего выполнения шага.|  
|**proxy_id**|**int**|Учетная запись-посредник для шага задания.|  
|**step_uid**|**uniqueidentifier**|Идентификатор шага задания.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
