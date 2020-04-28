---
title: dbo. сисжобстепс (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 13cf57e181c3fbb1371c10b554eb9da344a951d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68004734"
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения для каждого этапа задания, исполняемого агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**step_id**|**int**|Идентификатор этапа в задании.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**подсистемы**|**nvarchar(40)**|Имя подсистемы, используемой агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения шага задания.|  
|**кнопки**|**nvarchar(max)**|Команда, выполняемая **подсистемой**.|  
|**flags**|**int**|Зарезервировано.|  
|**additional_parameters**|**ntext**|Зарезервировано.|  
|**cmdexec_success_code**|**int**|Значение уровня ошибки, возвращаемое шагами подсистемы **CmdExec** для обозначения успеха.|  
|**on_success_action**|**tinyint**|Действие, выполняемое в случае успешного завершения шага.|  
|**on_success_step_id**|**int**|Идентификатор следующего этапа, выполняемого в случае успешного завершения шага.|  
|**on_fail_action**|**tinyint**|Действие, выполняемое в случае неуспешного завершения шага.|  
|**on_fail_step_id**|**int**|Идентификатор следующего этапа, выполняемого в случае неуспешного завершения шага.|  
|**сервером**|**sysname**|Зарезервировано.|  
|**database_name**|**sysname**|Имя базы данных, в которой выполняется **команда** , если в качестве **подсистемы** используется TSQL.|  
|**database_user_name**|**sysname**|Имя пользователя базы данных, чья учетная запись будет использоваться для выполнения шага.|  
|**retry_attempts**|**int**|Число попыток повтора при неуспешном завершении шага.|  
|**retry_interval**|**int**|Время ожидания между попытками повтора.|  
|**os_run_priority**|**int**|Зарезервировано.|  
|**output_file_name**|**nvarchar(200)**|Имя файла, в котором сохраняются выходные данные этапа, если **подсистема** — TSQL, PowerShell или **CmdExec**_._|  
|**last_run_outcome**|**int**|Результат предыдущего выполнения шага задания.<br /><br /> **0** = сбой<br /><br /> **1** = успех<br /><br /> **2** = повторная попытка<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_run_duration**|**int**|Продолжительность (ччммсс) шага в секундах при последнем запуске.|  
|**last_run_retries**|**int**|Число попыток повтора в ходе последнего выполнения шага задания.|  
|**last_run_date**|**int**|Дата начала (ггггммдд) последнего выполнения шага.|  
|**last_run_time**|**int**|Время начала (ччммсс) последнего выполнения шага.|  
|**proxy_id**|**int**|Учетная запись-посредник для шага задания.|  
|**step_uid**|**uniqueidentifier**|Идентификатор шага задания.|  
  
## <a name="see-also"></a>См. также:  
 [Агент SQL Serverные таблицы &#40;&#41;Transact-SQL](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
