---
title: "dbo.sysjobsteps (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4f316e40cc6bf89cf7296b5a2d864406142f7f87
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения для каждого этапа задания, исполняемого агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Аргумент job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**step_id**|**int**|Идентификатор этапа в задании.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**Подсистема**|**nvarchar(40)**|Имя подсистемы, используемой агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения шага задания.|  
|**команда**|**nvarchar(max)**|Команда для выполнения по **подсистемы**.|  
|**флаги**|**int**|Зарезервировано.|  
|**additional_parameters**|**ntext**|Зарезервировано.|  
|**cmdexec_success_code**|**int**|Значение уровня ошибки, возвращенные **CmdExec** подсистемы действия в случае успеха.|  
|**on_success_action**|**tinyint**|Действие, выполняемое в случае успешного завершения шага.|  
|**on_success_step_id**|**int**|Идентификатор следующего этапа, выполняемого в случае успешного завершения шага.|  
|**on_fail_action**|**tinyint**|Действие, выполняемое в случае неуспешного завершения шага.|  
|**on_fail_step_id**|**int**|Идентификатор следующего этапа, выполняемого в случае неуспешного завершения шага.|  
|**сервер**|**sysname**|Зарезервировано.|  
|**database_name**|**sysname**|Имя базы данных, в котором **команда** выполняется, если **подсистемы** является TSQL.|  
|**database_user_name**|**sysname**|Имя пользователя базы данных, чья учетная запись будет использоваться для выполнения шага.|  
|**retry_attempts**|**int**|Число попыток повтора при неуспешном завершении шага.|  
|**интервал_повтора**|**int**|Время ожидания между попытками повтора.|  
|**os_run_priority**|**int**|Зарезервировано.|  
|**имя_выходного_файла**|**nvarchar(200)**|Имя файла, в котором выходные данные этапа, сохраняется **подсистемы** является TSQL, PowerShell или **CmdExec***.*|  
|**last_run_outcome**|**int**|Результат предыдущего выполнения шага задания.<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **2** = Повтор<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_run_duration**|**int**|Продолжительность (ччммсс) шага в секундах при последнем запуске.|  
|**last_run_retries**|**int**|Число попыток повтора в ходе последнего выполнения шага задания.|  
|**last_run_date**|**int**|Дата начала (ггггммдд) последнего выполнения шага.|  
|**last_run_time**|**int**|Время начала (ччммсс) последнего выполнения шага.|  
|**proxy_id**|**int**|Учетная запись-посредник для шага задания.|  
|**step_uid**|**uniqueidentifier**|Идентификатор шага задания.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы агента SQL Server &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
