---
title: sp_help_jobs_in_schedule (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobs_in_schedule_TSQL
- sp_help_jobs_in_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobs_in_schedule
ms.assetid: 1168aa2c-136b-4ba3-b18e-9070d95a26fa
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78bffc1432bb650d5c1a7f37c0a712c34236dca1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobsinschedule-transact-sql"></a>sp_help_jobs_in_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о заданиях, присоединенных к определенному расписанию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobs_in_schedule   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@schedule_id =** ] *schedule_id*  
 Идентификатор расписания, о котором необходимо вывести сведения. *schedule_id* — **int**, не имеет значения по умолчанию. Либо *schedule_id* или *schedule_name* может быть указан.  
  
 [  **@schedule_name =** ] **"***schedule_name***"**  
 Имя расписания, о котором необходимо вывести сведения. *schedule_name* — **sysname**, не имеет значения по умолчанию. Либо *schedule_id* или *schedule_name* может быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания.|  
|**originating_server**|**nvarchar(30)**|Имя сервера, от которого поступило задание.|  
|**name**|**sysname**|Имя задания.|  
|**Включен**|**tinyint**|Показывает, разрешено ли задание к выполнению.|  
|**Описание**|**nvarchar(512)**|Описание задания.|  
|**start_step_id**|**int**|Идентификатор шага задания, с которого должно начаться выполнение.|  
|**Категория**|**sysname**|Категория задания.|  
|**Владелец**|**sysname**|Владелец задания.|  
|**notify_level_eventlog**|**int**|Битовая маска, указывающая, при каких обстоятельствах событие уведомления должно записываться в журнал приложений Microsoft Windows. Может принимать одно из следующих значений:<br /><br /> **0** = никогда<br /><br /> **1** = при успешном выполнении задания;<br /><br /> **2** = при ошибке задания<br /><br /> **3** = каждый раз по завершении задания (вне зависимости от результата выполнения)|  
|**notify_level_email**|**int**|Битовая маска, показывающая, при каких обстоятельствах должно посылаться уведомление по электронной почте при завершении выполнения задания. Возможные значения: аналогичны **notify_level_eventlog**.|  
|**notify_level_netsend**|**int**|Битовая маска, показывающая, при каких обстоятельствах должно посылаться сообщение по сети при завершении выполнения задания. Возможные значения: аналогичны **notify_level_eventlog**.|  
|**notify_level_page**|**int**|Битовая маска, показывающая, при каких обстоятельствах должно посылаться сообщение на пейджер при завершении выполнения задания. Возможные значения: аналогичны **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|Имя адреса электронной почты уведомляемого оператора.|  
|**notify_netsend_operator**|**sysname**|Имя компьютера или пользователя, используемое при отправке сетевых сообщений.|  
|**notify_page_operator**|**sysname**|Имя компьютера или пользователя, используемое при отправке сообщения на пейджер.|  
|**delete_level**|**int**|Битовая маска, показывающая, при каких обстоятельствах задание должно удаляться при завершении выполнения задания. Возможные значения: аналогичны **notify_level_eventlog**.|  
|**date_created**|**datetime**|Дата создания задания.|  
|**date_modified**|**datetime**|Дата последнего изменения задания.|  
|**version_number**|**int**|Версия задания (автоматически обновляется каждый раз при изменении задания).|  
|**last_run_date**|**int**|Дата последнего запуска задания на выполнение.|  
|**last_run_time**|**int**|Время последнего запуска задания на выполнение.|  
|**last_run_outcome**|**int**|Результат последнего выполнения задания:<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**next_run_date**|**int**|Дата следующего запуска задания по расписанию.|  
|**next_run_time**|**int**|Время следующего запуска задания по расписанию.|  
|**next_run_schedule_id**|**int**|Идентификационный номер следующего запуска по расписанию.|  
|**current_execution_status**|**int**|Текущее состояние выполнения.|  
|**current_execution_step**|**sysname**|Текущий этап выполнения задания.|  
|**current_retry_attempt**|**int**|Если задание выполняется и этап был повторен — это текущая попытка повтора.|  
|**has_step**|**int**|Число шагов в задании.|  
|**has_schedule**|**int**|Число назначенных запусков задания в расписании.|  
|**has_target**|**int**|Число целевых серверов в задании.|  
|**type**|**int**|Тип задания:<br /><br /> **1** = локальное задание.<br /><br /> **2** = многосерверное задание.<br /><br /> **0** = задание не имеет целевых серверов.|  
  
## <a name="remarks"></a>Замечания  
 Эта процедура заносит в список сведения о заданиях, присоединенных к указанному расписанию.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** можно просматривать состояние только тех заданий, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
 В следующем примере в список заносятся задания, присоединенные к расписанию `NightlyJobs`.   
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobs_in_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [процедуру sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
