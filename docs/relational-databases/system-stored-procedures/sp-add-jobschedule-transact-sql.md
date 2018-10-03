---
title: sp_add_jobschedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_jobschedule
- sp_add_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobschedule
ms.assetid: ffce19d9-d1d6-45b4-89fd-ad0f60822ba0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e52684ee8c73c976e42c29ca54079ac716527a1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834492"
---
# <a name="spaddjobschedule-transact-sql"></a>sp_add_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает расписание выполнения задания.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_jobschedule [ @job_id = ] job_id, | [ @job_name = ] 'job_name', [ @name = ] 'name'  
     [ , [ @enabled = ] enabled_flag ]  
     [ , [ @freq_type = ] frequency_type ]  
     [ , [ @freq_interval = ] frequency_interval ]  
     [ , [ @freq_subday_type = ] frequency_subday_type ]  
     [ , [ @freq_subday_interval = ] frequency_subday_interval ]  
     [ , [ @freq_relative_interval = ] frequency_relative_interval ]  
     [ , [ @freq_recurrence_factor = ] frequency_recurrence_factor ]  
     [ , [ @active_start_date = ] active_start_date ]  
     [ , [ @active_end_date = ] active_end_date ]  
     [ , [ @active_start_time = ] active_start_time ]  
     [ , [ @active_end_time = ] active_end_time ]  
     [ , [ @schedule_id = ] schedule_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id=** ] *job_id*  
 Идентификационный номер задания, которому добавляется расписание. *job_id* — **uniqueidentifier**, не имеет значения по умолчанию.  
  
 [  **@job_name=** ] **"***имя_задания***"**  
 Имя задания, которому добавляется расписание. *имя_задания* — **nvarchar(128)**, не имеет значения по умолчанию.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@name=** ] **"***имя***"**  
 Имя расписания. *имя* — **nvarchar(128)**, не имеет значения по умолчанию.  
  
 [  **@enabled=** ] *enabled_flag*  
 Отображает текущее состояние расписания. *enabled_flag* — **tinyint**, значение по умолчанию **1** (включено). Если **0**, расписание не включено. Если расписание отключено, то задание не выполняется.  
  
 [  **@freq_type=** ] *frequency_type*  
 Это значение указывает, когда должно выполняться задание. *frequency_type* — **int**, значение по умолчанию **0**, и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно, относительно *frequency_interval.*|  
|**64**|Выполняется при запуске службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**128**|Запускается при простое компьютера.|  
  
 [  **@freq_interval=** ] *frequency_interval*  
 Дни, когда выполняется задание. *frequency_interval* — **int**, значение по умолчанию 0 и зависит от значения *frequency_type* как указано в следующей таблице:  
  
|Значение|Действие|  
|-----------|------------|  
|**1** (один раз)|*frequency_interval* не используется.|  
|**4** (ежедневно)|Каждый *frequency_interval* дней.|  
|**8** (еженедельно)|*frequency_interval* равно одному или нескольким из следующих (объединены логическим оператором OR):<br /><br /> 1 = воскресенье<br /><br /> 2 = понедельник<br /><br /> 4 = Вторник<br /><br /> 8 = среда<br /><br /> 16 = четверг<br /><br /> 32 = Пятница<br /><br /> 64 = суббота|  
|**16** (ежемесячно)|На *frequency_interval* день месяца.|  
|**32** (относительно ежемесячно)|*frequency_interval* является одним из следующих:<br /><br /> 1 = воскресенье<br /><br /> 2 = понедельник<br /><br /> 3 = вторник<br /><br /> 4 = среда<br /><br /> 5 = четверг<br /><br /> 6 = пятница<br /><br /> 7 = суббота<br /><br /> 8 = Ежедневно<br /><br /> 9 = рабочий день<br /><br /> 10 = выходной|  
|**64** (при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуске службы агента)|*frequency_interval* не используется.|  
|**128**|*frequency_interval* не используется.|  
  
 [ **@freq_subday_type=** ] *frequency_subday_type*  
 Указывает единицы измерения для *frequency_subday_interval*. *frequency_subday_type* — **int**, по умолчанию и может принимать одно из следующих значений:  
  
|Значение|Описание (единица измерения)|  
|-----------|--------------------------|  
|**0x1**|В указанное время|  
|**0x4**|Минуты|  
|**0x8**|Часы|  
  
 [  **@freq_subday_interval=** ] *frequency_subday_interval*  
 Число *frequency_subday_type* периодов должно пройти между выполнениями задания. *frequency_subday_interval* — **int**, значение по умолчанию 0.  
  
 [  **@freq_relative_interval=** ] *frequency_relative_interval*  
 Далее описывается *frequency_interval* при *frequency_type* присваивается **32** (относительно ежемесячно).  
  
 *frequency_relative_interval* — **int**, по умолчанию и может принимать одно из следующих значений:  
  
|Значение|Описание (единица измерения)|  
|-----------|--------------------------|  
|**1**|Первая|  
|**2**|Вторая|  
|**4**|Третья|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
 *frequency_relative_interval* показывает вхождения интервалов. Например если *frequency_relative_interval* присваивается **2**, *frequency_type* присваивается **32**, и *frequency_ интервал* присваивается **3**, планируемые задания будут выполняться во второй вторник каждого месяца.  
  
 [  **@freq_recurrence_factor=** ] *frequency_recurrence_factor*  
 Число недель или месяцев между запланированными выполнениями задания. *frequency_recurrence_factor* используется только в том случае, если *frequency_type* присваивается **8**, **16**, или **32**. *frequency_recurrence_factor* — **int**, значение по умолчанию 0.  
  
 [  **@active_start_date=** ] *active_start_date*  
 Дата, когда может начаться выполнение задания. *active_start_date* — **int**, не имеет значения по умолчанию. Формат даты: ГГГГMMДД. Если *active_start_date* не установлен, дата должна быть больше или равна 19900101.  
  
 После создания расписания проверьте дату начала и убедитесь, что она задана правильно. Дополнительные сведения см в разделе «Планирование даты начала» [Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 [  **@active_end_date=** ] *active_end_date*  
 Дата, когда может быть остановлено выполнение задания. *active_end_date* — **int**, не имеет значения по умолчанию. Формат даты: ГГГГMMДД.  
  
 [  **@active_start_time=** ] *active_start_time*  
 Время в любой день между *active_start_date* и *active_end_date* начала выполнения задания. *active_start_time* — **int**, не имеет значения по умолчанию. Формат времени ЧЧMMСС в 24-часовом формате.  
  
 [**@active_end_time= *** active_end_time*  
 Время в любой день между *active_start_date* и *active_end_date* окончания выполнения задания. *active_end_time* — **int**, не имеет значения по умолчанию. Формат времени ЧЧMMСС в 24-часовом формате.  
  
 [  **@schedule_id=***schedule_id***выходных данных**  
 Идентификационный номер, присваиваемый учетной записи-посреднику после успешного создания. *schedule_id* является выходной переменной типа **int**, не имеет значения по умолчанию.  
  
 [ **@schedule_uid**=] *schedule_uid *** выходных данных**  
 Уникальный идентификатор для расписания. *schedule_uid* является переменной типа **uniqueidentifier**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Расписанием задач теперь можно управлять независимо от них самих. Чтобы добавить расписание задания, используйте **sp_add_schedule** для создания расписания и **sp_attach_schedule** Чтобы присоединить расписание к заданию.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
 
 ## <a name="example"></a>Пример
 В следующем примере назначается, чтобы расписание задания `SaturdayReports` которой будет выполнен каждую субботу в 2 часа НОЧИ.
```sql  
EXEC msdb.dbo.sp_add_jobschedule 
        @job_name = N'SaturdayReports', -- Job name
        @name = N'Weekly_Sat_2AM',  -- Schedule name
        @freq_type = 8, -- Weekly
        @freq_interval = 64, -- Saturday
        @freq_recurrence_factor = 1, -- every week
        @active_start_time = 20000 -- 2:00 AM
```
  
## <a name="see-also"></a>См. также  
 [Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Планирование выполнения заданий](../../ssms/agent/schedule-a-job.md)   
 [Создание расписания](../../ssms/agent/create-a-schedule.md)   
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
