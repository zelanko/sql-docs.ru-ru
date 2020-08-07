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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f69b827981a53024dbf22d4b3e3d2f64fd4b720f
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87865123"
---
# <a name="sp_add_jobschedule-transact-sql"></a>sp_add_jobschedule (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает расписание для задания агента SQL Server.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  > [!IMPORTANT]  
  > В [Azure SQL управляемый экземпляр](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), в настоящее время поддерживаются не все функции агент SQL Server. Дополнительные сведения см. [в статье отличия T-sql управляемый экземпляр SQL Azure от SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) .

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
     [ , [ @schedule_uid = ] _schedule_uid OUTPUT ]
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания, к которому добавляется расписание. *job_id* имеет тип **uniqueidentifier**и не имеет значения по умолчанию.  
  
`[ @job_name = ] 'job_name'`Имя задания, к которому добавляется расписание. *job_name* имеет тип **nvarchar (128)** и не имеет значения по умолчанию.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @name = ] 'name'`Имя расписания. *имя* имеет тип **nvarchar (128)** и не имеет значения по умолчанию.  
  
`[ @enabled = ] enabled_flag`Указывает текущее состояние расписания. *enabled_flag* имеет тип **tinyint**и значение по умолчанию **1** (включено). Если значение **равно 0**, расписание не включено. Если расписание отключено, то задание не выполняется.  
  
`[ @freq_type = ] frequency_type`Значение, указывающее, когда должно выполняться задание. *frequency_type* имеет **тип int**, значение по умолчанию **0**и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Однократно|  
|**4**|Ежедневно|  
|**8**|Еженедельно|  
|**16**|Ежемесячно|  
|**32**|Ежемесячно относительно *frequency_interval.*|  
|**64**|Выполняется при запуске службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**128**|Запускается при простое компьютера.|  
  
`[ @freq_interval = ] frequency_interval`День выполнения задания. *frequency_interval* имеет **тип int**, значение по умолчанию 0 и зависит от значения *frequency_type* , как указано в следующей таблице.  
  
|Значение|Действие|  
|-----------|------------|  
|**1** (один раз)|*frequency_interval* не используется.|  
|**4** (ежедневно)|Каждые *frequency_interval* дней.|  
|**8** (еженедельно)|*frequency_interval* является одним или несколькими следующими (в сочетании с логическим оператором OR):<br /><br /> 1 = воскресенье<br /><br /> 2 = понедельник<br /><br /> 4 = вторник<br /><br /> 8 = среда<br /><br /> 16 = Четверг<br /><br /> 32 = Пятница<br /><br /> 64 = суббота|  
|**16** (ежемесячно)|В *frequency_interval* день месяца.|  
|**32** (ежемесячная относительная)|*frequency_interval* является одним из следующих:<br /><br /> 1 = воскресенье<br /><br /> 2 = понедельник<br /><br /> 3 = вторник<br /><br /> 4 = среда<br /><br /> 5 = четверг<br /><br /> 6 = пятница<br /><br /> 7 = суббота<br /><br /> 8 = Ежедневно<br /><br /> 9 = рабочий день<br /><br /> 10 = выходной|  
|**64** (при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуске службы агента)|*frequency_interval* не используется.|  
|**128**|*frequency_interval* не используется.|  
  
`[ @freq_subday_type = ] frequency_subday_type`Указывает единицы для *frequency_subday_interval*. *frequency_subday_type* имеет **тип int**, не имеет значения по умолчанию и может принимать одно из следующих значений:  
  
|Значение|Описание (единица измерения)|  
|-----------|--------------------------|  
|**0x1**|В указанное время|  
|**0x4**|Минуты|  
|**0x8**|Часы|  
  
`[ @freq_subday_interval = ] frequency_subday_interval`Число периодов *frequency_subday_type* , которые должны быть выполнены между выполнением задания. *frequency_subday_interval* имеет **тип int**и значение по умолчанию 0.  
  
`[ @freq_relative_interval = ] frequency_relative_interval`Далее определяется *frequency_interval* , если *frequency_type* установлен в **32** (ежемесячное относительное значение).  
  
 *frequency_relative_interval* имеет **тип int**, не имеет значения по умолчанию и может принимать одно из следующих значений:  
  
|Значение|Описание (единица измерения)|  
|-----------|--------------------------|  
|**1**|First|  
|**2**|Секунда|  
|**4**|Третье|  
|**8**|Четвертая|  
|**16**|Последняя|  
  
 *frequency_relative_interval* указывает на вхождение интервала. Например, если *frequency_relative_interval* имеет значение **2**, *frequency_type* имеет значение **32**, а *frequency_interval* имеет значение **3**, запланированное задание будет выполняться во второй вторник каждого месяца.  
  
`[ @freq_recurrence_factor = ] frequency_recurrence_factor`Число недель или месяцев между запланированным выполнением задания. *frequency_recurrence_factor* используется только в том случае, если *frequency_type* имеет значение **8**, **16**или **32**. *frequency_recurrence_factor* имеет **тип int**и значение по умолчанию 0.  
  
`[ @active_start_date = ] active_start_date`Дата начала выполнения задания. *active_start_date* имеет **тип int**и не имеет значения по умолчанию. Формат даты: ГГГГMMДД. Если задан параметр *active_start_date* , дата должна быть больше или равна 19900101.  
  
 После создания расписания проверьте дату начала и убедитесь, что она задана правильно. Дополнительные сведения см. в подразделе «Дата начала планирования» раздела [Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
`[ @active_end_date = ] active_end_date`Дата, когда выполнение задания может быть прервано. *active_end_date* имеет **тип int**и не имеет значения по умолчанию. Формат даты: ГГГГMMДД.  
  
`[ @active_start_time = ] active_start_time`Время в любой день между *active_start_date* и *active_end_date* , чтобы начать выполнение задания. *active_start_time* имеет **тип int**и не имеет значения по умолчанию. Формат времени ЧЧMMСС в 24-часовом формате.  
  
`[ @active_end_time = active_end_time_`Время в любой день между *active_start_date* и *active_end_date* , чтобы завершить выполнение задания. *active_end_time* имеет **тип int**и не имеет значения по умолчанию. Формат времени ЧЧMMСС в 24-часовом формате.  
  
`[ @schedule_id = schedule_idOUTPUT`Запланировать идентификационный номер, назначенный для расписания, если он успешно создан. *schedule_id* является выходной переменной типа **int**и не имеет значения по умолчанию.  
  
`[ @schedule_uid = ] _schedule_uidOUTPUT`Уникальный идентификатор расписания. *schedule_uid* является переменной типа **uniqueidentifier**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Расписанием задач теперь можно управлять независимо от них самих. Чтобы добавить расписание к заданию, используйте **sp_add_schedule** , чтобы создать расписание и **sp_attach_schedule** присоединить расписание к заданию.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
 
 ## <a name="example"></a>Пример
 В следующем примере назначается расписание задания, `SaturdayReports` которое будет выполняться каждую субботу в 2:00 AM.
```sql  
EXEC msdb.dbo.sp_add_jobschedule 
        @job_name = N'SaturdayReports', -- Job name
        @name = N'Weekly_Sat_2AM',  -- Schedule name
        @freq_type = 8, -- Weekly
        @freq_interval = 64, -- Saturday
        @freq_recurrence_factor = 1, -- every week
        @active_start_time = 20000 -- 2:00 AM
```
  
## <a name="see-also"></a>См. также:  
 [Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Планирование задания](../../ssms/agent/schedule-a-job.md)   
 [Создание расписания](../../ssms/agent/create-a-schedule.md)   
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
