---
title: sp_help_jobstep (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b7313e3784c5af9922fb5301b339087510a98e91
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773828"
---
# <a name="sp_help_jobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения об этапах задания, используемых службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для автоматизации выполнения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] 'job_id'`Идентификационный номер задания, для которого возвращаются сведения о задании. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @step_id = ] step_id`Идентификационный номер этапа в задании. Если не указан, включаются все этапы задания. *step_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @step_name = ] 'step_name'`Имя шага в задании. Аргумент *step_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @suffix = ] suffix`Флаг, указывающий, добавляется ли текстовое описание к столбцу **flags** в выходных данных. *суффикс*имеет **битовую**длину и значение по умолчанию **0**. Если *суффикс* имеет значение **1**, добавляется описание.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Уникальный идентификатор шага.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**подсистемы**|**nvarchar(40)**|Подсистема, в которой выполняется команда этапа.|  
|**command**|**nvarchar(max)**|Выполняемая на шаге команда.|  
|**flags**|**int**|Битовая маска значений, управляющая режимом шага.|  
|**cmdexec_success_code**|**int**|Для шага **CmdExec** это код завершения процесса успешной команды.|  
|**on_success_action**|**tinyint**|Операция, выполняемая в случае успешного завершении шага:<br /><br /> **1** = завершить задание с сообщением об успешном завершении.<br /><br /> **2** = завершить задание отчета о сбое.<br /><br /> **3** = перейти к следующему шагу.<br /><br /> **4** = перейти к шагу.|  
|**on_success_step_id**|**int**|Если значение **on_success_action** равно 4, это указывает на следующий шаг для выполнения.|  
|**on_fail_action**|**tinyint**|Операция, совершаемая в случае сбоя при выполнении шага. Значения совпадают с **on_success_action**.|  
|**on_fail_step_id**|**int**|Если значение **on_fail_action** равно 4, это указывает на следующий шаг для выполнения.|  
|**server**|**sysname**|Зарезервировано.|  
|**database_name**|**sysname**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] это база данных, в которой выполняется команда.|  
|**database_user_name**|**sysname**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] это контекст пользователя базы данных, в котором выполняется команда.|  
|**retry_attempts**|**int**|Максимальное количество повторных попыток выполнения команды (в случае сбоев).|  
|**retry_interval**|**int**|Интервал (в минутах) между повторными попытками.|  
|**os_run_priority**|**int**|Зарезервировано.|  
|**output_file_name**|**nvarchar(200)**|Файл, в который должны быть записаны выходные данные команды ( [!INCLUDE[tsql](../../includes/tsql-md.md)] только шаги **CmdExec**и **PowerShell** ).|  
|**last_run_outcome**|**int**|Результат последнего запуска этапа:<br /><br /> **0** = сбой<br /><br /> **1** = успех<br /><br /> **2** = повторная попытка<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_run_duration**|**int**|Продолжительность (ччммсс) шага в секундах при последнем запуске.|  
|**last_run_retries**|**int**|Число повторов команды при последнем запуске этапа.|  
|**last_run_date**|**int**|Дата начала последнего выполнения этапа.|  
|**last_run_time**|**int**|Время начала последнего выполнения этапа.|  
|**proxy_id**|**int**|Учетная запись-посредник для шага задания.|  
  
## <a name="remarks"></a>Примечания  
 **sp_help_jobstep** находится в базе данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены группы **SQLAgentUserRole** могут просматривать только шаги заданий, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. Возврат сведений обо всех шагах указанного задания  
 В следующем примере возвращаются все шаги задания с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>Б. Возврат сведений об указанном шаге задания  
 В следующем примере возвращаются сведения о первом шаге задания с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
