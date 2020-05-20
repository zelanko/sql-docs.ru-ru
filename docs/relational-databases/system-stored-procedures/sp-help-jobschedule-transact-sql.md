---
title: sp_help_jobschedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobschedule
- sp_help_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobschedule
ms.assetid: 2cded902-9272-4667-ac4b-a4f95a9f008e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 30ffe0203b3f9aacf23d811e48e6e6d8094a4ee2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827615"
---
# <a name="sp_help_jobschedule-transact-sql"></a>sp_help_jobschedule (Transact-SQL)
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
`[ @job_id = ] job_id`Идентификационный номер задания. *job_id*имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]
> Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.

`[ @schedule_name = ] 'schedule_name'`Имя элемента расписания для задания. Аргумент *schedule_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @schedule_id = ] schedule_id`Идентификационный номер элемента расписания для задания. *schedule_id*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @include_description = ] include_description`Указывает, следует ли включать описание расписания в результирующий набор. *include_description* имеет **бит**и значение по умолчанию **0**. Если *include_description* равен **0**, описание расписания не включается в результирующий набор. Если *include_description* равен **1**, описание расписания включается в результирующий набор.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификационный номер расписания.|  
|**schedule_name**|**sysname**|Имя расписания.|  
|**доступной**|**int**|Включено ли расписание (**1**) или не включено (**0**).|  
|**freq_type**|**int**|Значение, указывающее, когда должно выполняться задание.<br /><br /> **1** = один раз<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячно относительно **freq_interval**<br /><br /> **64** = запуск при запуске службы **SQLServerAgent** .|  
|**freq_interval**|**int**|Дни, в которые выполняется задание. Значение зависит от значения **freq_type**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_type**|**int**|Единицы для **freq_subday_interval**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_subday_interval**|**int**|Число периодов **freq_subday_type** , которые должны быть выполнены между выполнением задания. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_relative_interval**|**int**|Вхождение **freq_interval** запланированного задания в каждый месяц. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md).|  
|**freq_recurrence_factor**|**int**|Число месяцев между выполнениями задания по расписанию.|  
|**active_start_date**|**int**|Дата, когда начинает действовать расписание.|  
|**active_end_date**|**int**|Дата, когда прекращает действовать расписание.|  
|**active_start_time**|**int**|Время суток, когда начинает действовать расписание.|  
|**active_end_time**|**int**|Время суток, когда прекращает действовать расписание.|  
|**date_created**|**datetime**|Дата создания расписания.|  
|**schedule_description**|**nvarchar(4000)**|Описание расписания на английском языке, полученное из значений в **msdb. dbo. sysschedules**. Если значение *include_description* равно **0**, этот столбец содержит текст, указывающий, что описание не было запрошено.|  
|**next_run_date**|**int**|Дата следующего выполнения задания в соответствии с расписанием.|  
|**next_run_time**|**int**|Время следующего выполнения задания в соответствии с расписанием.|  
|**schedule_uid**|**uniqueidentifier**|Идентификатор расписания.|  
|**job_count**|**int**|Возвращенное количество заданий.|  
  
> **Примечание. sp_help_jobschedule** возвращает значения из системных таблиц **dbo. sysjobschedules** и **dbo. sysschedules** в **базе данных msdb**. **sysjobschedules** обновляются каждые 20 минут. Это может повлиять на значения, возвращаемые этой хранимой процедурой.  
  
## <a name="remarks"></a>Примечания  
 Параметры **sp_help_jobschedule** могут использоваться только в определенных сочетаниях. Если указан *schedule_id* , нельзя указать ни *job_id* , ни *job_name* . В противном случае можно использовать параметры *job_id* или *job_name* с *schedule_name*.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены **SQLAgentUserRole** могут только просматривать свойства расписаний заданий, которыми они владеют.  
  
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
