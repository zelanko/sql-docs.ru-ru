---
title: sp_help_jobschedule (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobschedule
- sp_help_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobschedule
ms.assetid: 2cded902-9272-4667-ac4b-a4f95a9f008e
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: edaebbc89b6422bd529963dc851371747f7d22be
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobschedule-transact-sql"></a>sp_help_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о расписании выполнения заданий, используемом средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для выполнения автоматических действий.  
 
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobschedule { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @schedule_name = ] 'schedule_name' ]  
     [ , [ @schedule_id = ] schedule_id ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id=** ] *job_id*  
 Идентификационный номер задания. *Аргумент job_id*— **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name=** ] **"***job_name***"**  
 Имя задания. *job_name*— **sysname**, значение по умолчанию NULL.  
  
> **Примечание:** либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@schedule_name=** ] **"***schedule_name***"**  
 Имя элемента расписания для задания. *schedule_name*— **sysname**, значение по умолчанию NULL.  
  
 [  **@schedule_id=** ] *schedule_id*  
 Идентификатор элемента расписания для задания. *schedule_id*— **int**, значение по умолчанию NULL.  
  
 [  **@include_description=** ] *этот аргумент*  
 Указывает, нужно ли включать описание расписания в результирующий набор. *Этот аргумент* — **бит**, значение по умолчанию **0**. Когда *этот аргумент* — **0**, описание расписания не включается в результирующий набор. Когда *этот аргумент* — **1**, в результирующий набор включается описание расписания.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификационный номер расписания.|  
|**schedule_name**|**sysname**|Имя расписания.|  
|**Включен**|**int**|Расписание задействовано (**1**) или не включено (**0**).|  
|**freq_type**|**int**|Значение, указывающее, когда должно выполняться задание.<br /><br /> **1** = однократно<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячно, относительно **freq_interval**<br /><br /> **64** = выполнять, когда **SQLServerAgent** запуске службы.|  
|**freq_interval**|**int**|Дни, в которые выполняется задание. Значение зависит от значения **freq_type**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Единицы измерения для **freq_subday_interval**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Число **freq_subday_type** периодов должно пройти между выполнениями задания. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Запланированные задания **freq_interval** в каждом месяце. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**int**|Число месяцев между выполнениями задания по расписанию.|  
|**active_start_date**|**int**|Дата, когда начинает действовать расписание.|  
|**active_end_date**|**int**|Дата, когда прекращает действовать расписание.|  
|**active_start_time**|**int**|Время суток, когда начинает действовать расписание.|  
|**active_end_time**|**int**|Время суток, когда прекращает действовать расписание.|  
|**date_created**|**datetime**|Дата создания расписания.|  
|**schedule_description**|**nvarchar(4000)**|Описание на английском языке расписание, которое является производным от значений в **msdb.dbo.sysschedules**. Когда *этот аргумент* — **0**, этот столбец содержит текст, указывающий, что описание не было запрошено.|  
|**next_run_date**|**int**|Дата следующего выполнения задания в соответствии с расписанием.|  
|**next_run_time**|**int**|Время следующего выполнения задания в соответствии с расписанием.|  
|**schedule_uid**|**uniqueidentifier**|Идентификатор расписания.|  
|**job_count**|**int**|Возвращенное количество заданий.|  
  
> **Примечание:****sp_help_jobschedule** возвращает значения из **dbo.sysjobschedules** и **dbo.sysschedules** системных таблиц в **базы данных msdb** . **sysjobschedules** обновляется каждые 20 минут. Это может повлиять на значения, возвращаемые этой хранимой процедурой.  
  
## <a name="remarks"></a>Замечания  
 Параметры **sp_help_jobschedule** может использоваться только в определенных сочетаниях. Если *schedule_id* указано, ни *job_id* , ни *job_name* можно указать. В противном случае *job_id* или *job_name* параметры могут использоваться с *schedule_name*.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** могут лишь просматривать свойства расписаний заданий, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-job-schedule-for-a-specific-job"></a>A. Возвращение расписания задания для конкретного задания  
 Следующий пример возвращает сведения о расписании для задания с именем `BackupDatabase`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule  
    @job_name = N'BackupDatabase' ;  
GO  
```  
  
### <a name="b-returning-the-job-schedule-for-a-specific-schedule"></a>Б. Возвращение расписания задания для конкретного расписания  
 Следующий пример возвращает сведения о расписании с названием `NightlyJobs` и задании с названием `RunReports`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule   
    @job_name = N'RunReports',  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="c-returning-the-job-schedule-and-schedule-description-for-a-specific-schedule"></a>В. Возвращение расписания задания и описания расписания для конкретного расписания  
 Следующий пример возвращает сведения о расписании с названием `NightlyJobs` и задании с названием `RunReports`. Возвращаемый результирующий набор включает описание расписания.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule  
    @job_name = N'RunReports',  
    @schedule_name = N'NightlyJobs',  
    @include_description = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
