---
title: sp_help_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_job_TSQL
- sp_help_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_job
ms.assetid: 8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6fe10c33c617833754ac23592528519aeabec1d5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893713"
---
# <a name="sp_help_job-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о заданиях, используемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения автоматических действий в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_job { [ @job_id = ] job_id  
[ @job_name = ] 'job_name' }   
     [ , [ @job_aspect = ] 'job_aspect' ]   
     [ , [ @job_type = ] 'job_type' ]   
     [ , [ @owner_login_name = ] 'login_name' ]   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @enabled = ] enabled ]   
     [ , [ @execution_status = ] status ]   
     [ , [ @date_comparator = ] 'date_comparison' ]   
     [ , [ @date_created = ] date_created ]   
     [ , [ @date_last_modified = ] date_modified ]   
     [ , [ @description = ] 'description_pattern' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Чтобы просмотреть конкретное задание, необходимо указать либо *job_id* , либо *job_name* .  Пропустите *job_id* и *job_name* , чтобы получить сведения обо всех заданиях.
  
`[ @job_aspect = ] 'job_aspect'`Атрибут задания для вывода. *job_aspect* имеет тип **varchar (9)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|**ALL**|Сведения об аспекте задания|  
|**ДОЛЖНО**|Сведения о задании|  
|**ДЕЙСТВИЕ**|Сведения о расписании|  
|**ВЫПОЛНЕНЫ**|Сведения об шаге задания|  
|**ЦЕЛИ**|Сведения о цели|  
  
`[ @job_type = ] 'job_type'`Тип заданий, включаемых в отчет. *job_type* имеет тип **varchar (12)** и значение по умолчанию NULL. *job_type* может быть **локальным** или **многосерверным**.  
  
`[ @owner_login_name = ] 'login_name'`Имя входа владельца задания. Аргумент *login_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @subsystem = ] 'subsystem'`Имя подсистемы. *подсистема* имеет тип **nvarchar (40)** и значение по умолчанию NULL.  
  
`[ @category_name = ] 'category'`Имя категории. *Category* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @enabled = ] enabled`Число, указывающее, отображаются ли сведения о включенных заданиях или отключенных заданиях. *Enabled* имеет тип **tinyint**и значение по умолчанию NULL. **1** указывает на включенные задания, а **0** означает отключенные задания.  
  
`[ @execution_status = ] status`Состояние выполнения заданий. *Status* имеет **тип int**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Возвращает только те задания, которые не находятся в состоянии бездействия или приостановки.|  
|**1**|Выполняющиеся.|  
|**2**|Ожидающие потока.|  
|**3**|Ожидающие повторной попытки.|  
|**4**|Бездействующие.|  
|**5**|Приостановленные.|  
|**7**|Выполняющие завершающие действия.|  
  
`[ @date_comparator = ] 'date_comparison'`Оператор сравнения, используемый в сравнениях *date_created* и *date_modified*. *date_comparison* имеет **тип char (1)** и может иметь значение =, \<, or > .  
  
`[ @date_created = ] date_created`Дата создания задания. *date_created*имеет тип **DateTime**и значение по умолчанию NULL.  
  
`[ @date_last_modified = ] date_modified`Дата последнего изменения задания. *date_modified* имеет тип **DateTime**и значение по умолчанию NULL.  
  
`[ @description = ] 'description_pattern'`Описание задания. *description_pattern* имеет тип **nvarchar (512)** и значение по умолчанию NULL. *description_pattern* может включать SQL Server подстановочных знаков для сопоставления шаблонов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если аргументы не указаны, **sp_help_job** возвращает этот результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания.|  
|**originating_server**|**nvarchar(30)**|Имя сервера, от которого поступило задание.|  
|**name**|**sysname**|Имя задания.|  
|**доступной**|**tinyint**|Показывает, разрешено ли задание к выполнению.|  
|**nописание**|**nvarchar(512)**|Описание задания.|  
|**start_step_id**|**int**|Идентификатор шага задания, с которого должно начаться выполнение.|  
|**category**|**sysname**|Категория задания.|  
|**владельцев**|**sysname**|Владелец задания.|  
|**notify_level_eventlog**|**int**|**Битовая маска** , указывающая, при каких обстоятельствах событие уведомления должно быть записано в журнал приложений Microsoft Windows. Может принимать одно из следующих значений:<br /><br /> **0** = никогда<br /><br /> **1** = при завершении задания;<br /><br /> **2** = при сбое задания<br /><br /> **3** = при завершении задания (независимо от результата задания);|  
|**notify_level_email**|**int**|**Битовая маска** , указывающая, при каких обстоятельствах необходимо отправить уведомление по электронной почте при завершении задания. Возможные значения: для **notify_level_eventlog**.|  
|**notify_level_netsend**|**int**|**Битовая маска** , указывающая, при каких обстоятельствах следует отправлять сетевое сообщение при завершении задания. Возможные значения: для **notify_level_eventlog**.|  
|**notify_level_page**|**int**|**Битовая маска** , указывающая, при каких обстоятельствах должна отправляться страница при завершении задания. Возможные значения: для **notify_level_eventlog**.|  
|**notify_email_operator**|**sysname**|Имя адреса электронной почты уведомляемого оператора.|  
|**notify_netsend_operator**|**sysname**|Имя компьютера или пользователя, используемое при отправке сетевых сообщений.|  
|**notify_page_operator**|**sysname**|Имя компьютера или пользователя, используемое при отправке сообщения на пейджер.|  
|**delete_level**|**int**|**Битовая маска** , указывающая, при каких обстоятельствах задание должно быть удалено после завершения задания. Возможные значения: для **notify_level_eventlog**.|  
|**date_created**|**datetime**|Дата создания задания.|  
|**date_modified**|**datetime**|Дата последнего изменения задания.|  
|**version_number**|**int**|Версия задания (автоматически обновляется каждый раз при изменении задания).|  
|**last_run_date**|**int**|Дата последнего запуска задания на выполнение.|  
|**last_run_time**|**int**|Время последнего запуска задания на выполнение.|  
|**last_run_outcome**|**int**|Результат последнего выполнения задания:<br /><br /> **0** = сбой<br /><br /> **1** = успех<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**next_run_date**|**int**|Дата следующего запуска задания по расписанию.|  
|**next_run_time**|**int**|Время следующего запуска задания по расписанию.|  
|**next_run_schedule_id**|**int**|Идентификационный номер следующего запуска по расписанию.|  
|**current_execution_status**|**int**|Текущее состояние выполнения:<br /><br /> **1** = исполнение<br /><br /> **2** = ожидание потока<br /><br /> **3** = между повторными попытками<br /><br /> **4** = бездействие<br /><br /> **5** = приостановлено<br /><br /> **6** = устарело<br /><br /> **7** = перформингкомплетионактионс|  
|**current_execution_step**|**sysname**|Текущий этап выполнения задания.|  
|**current_retry_attempt**|**int**|Если задание выполняется и этап был повторен — это текущая попытка повтора.|  
|**has_step**|**int**|Число шагов в задании.|  
|**has_schedule**|**int**|Число назначенных запусков задания в расписании.|  
|**has_target**|**int**|Число целевых серверов в задании.|  
|**type**|**int**|Тип задания.<br /><br /> 1 = Локальное задание.<br /><br /> **2** = многосерверное задание.<br /><br /> **0** = задание не имеет целевых серверов.|  
  
 Если указано *job_id* или *job_name* , **sp_help_job** возвращает эти дополнительные результирующие наборы для шагов задания, расписаний заданий и целевых серверов заданий.  
  
 Это результирующий набор для шагов задания.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Уникальный для данного задания идентификатор этапа.|  
|**step_name**|**sysname**|Имя этапа.|  
|**подсистемы**|**nvarchar(40)**|Подсистема, в которой выполняется команда этапа.|  
|**command**|**nvarchar (3200)**|Команда для выполнения.|  
|**flags**|**nvarchar(4000)**|**Битовая маска** значений, управляющих поведением шага.|  
|**cmdexec_success_code**|**int**|Для шага **CmdExec** это код завершения процесса успешной команды.|  
|**on_success_action**|**nvarchar(4000)**|Что делать в случае успешного выполнения этапа:<br /><br /> **1** = завершить успешно.<br /><br /> **2** = завершить с ошибкой.<br /><br /> **3** = перейти к следующему шагу.<br /><br /> **4** = перейти к шагу.|  
|**on_success_step_id**|**int**|Если значение **on_success_action** равно **4**, это указывает на следующий шаг для выполнения.|  
|**on_fail_action**|**nvarchar(4000)**|Действие, предпринимаемое в случае ошибки этапа. Значения совпадают с значениями для **on_success_action**.|  
|**on_fail_step_id**|**int**|Если значение **on_fail_action** равно **4**, это указывает на следующий шаг для выполнения.|  
|**server**|**sysname**|Зарезервировано.|  
|**database_name**|**sysname**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] это база данных, в которой выполняется команда.|  
|**database_user_name**|**sysname**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] это контекст пользователя базы данных, в котором выполняется команда.|  
|**retry_attempts**|**int**|Максимальное число попыток повтора команды (в случае неудачи) перед тем, как этап будет учтен как ошибочный.|  
|**retry_interval**|**int**|Интервал в минутах между попытками повтора.|  
|**os_run_priority**|**varchar (4000)**|Зарезервировано.|  
|**output_file_name**|**varchar (200)**|Файл, в который должны быть записаны выходные данные команды ( [!INCLUDE[tsql](../../includes/tsql-md.md)] только шаги **CmdExec** ).|  
|**last_run_outcome**|**int**|Результат последнего запуска этапа:<br /><br /> **0** = сбой<br /><br /> **1** = успех<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_run_duration**|**int**|Продолжительность этапа в секундах при последнем запуске.|  
|**last_run_retries**|**int**|Число повторов команды при последнем запуске этапа.|  
|**last_run_date**|**int**|Дата начала последнего выполнения этапа.|  
|**last_run_time**|**int**|Время начала последнего выполнения этапа.|  
|**proxy_id**|**int**|Учетная запись-посредник для шага задания.|  
  
 Это результирующий набор для расписания задания.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания (уникальный среди всех заданий).|  
|**schedule_name**|**sysname**|Имя расписания (уникально только для данного задания).|  
|**доступной**|**int**|Является ли расписание активным (**1**) или нет (**0**).|  
|**freq_type**|**int**|Значение, указывающее, как должно выполняться задание:<br /><br /> **1** = один раз<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячно относительно **freq_interval**<br /><br /> **64** = запуск при запуске службы **SQLServerAgent** .|  
|**freq_interval**|**int**|Дни, в которые выполняется задание. Значение зависит от значения **freq_type**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|Единицы для **freq_subday_interval**. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|Число периодов **freq_subday_type** , которые должны быть выполнены между выполнением задания. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|Вхождение **freq_interval** запланированного задания в каждый месяц. Дополнительные сведения см. в разделе [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|Число месяцев между выполнениями задания по расписанию.|  
|**active_start_date**|**int**|Дата начала выполнения задания.|  
|**active_end_date**|**int**|Дата завершения выполнения задания.|  
|**active_start_time**|**int**|Время начала выполнения задания на **active_start_date.**|  
|**active_end_time**|**int**|Время на завершение выполнения задания на **active_end_date**.|  
|**date_created**|**datetime**|Дата создания расписания.|  
|**schedule_description**|**nvarchar(4000)**|Описание расписания на английском языке (если запрошено).|  
|**next_run_date**|**int**|Дата следующего выполнения задания в соответствии с расписанием.|  
|**next_run_time**|**int**|Время следующего выполнения задания в соответствии с расписанием.|  
|**schedule_uid**|**uniqueidentifier**|Идентификатор расписания.|  
|**job_count**|**int**|Возвращает число заданий, ссылающихся на данное расписание.|  
  
 Это результирующий набор для целевых серверов задания.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор целевого сервера.|  
|**server_name**|**nvarchar(30)**|Имя компьютера целевого сервера.|  
|**enlist_date**|**datetime**|Дата прикрепления целевого сервера к главному серверу.|  
|**last_poll_date**|**datetime**|Дата последнего опроса главного сервера целевым сервером.|  
|**last_run_date**|**int**|Дата последнего запуска задания на выполнение на данном целевом сервере.|  
|**last_run_time**|**int**|Время последнего запуска задания на выполнение на данном целевом сервере.|  
|**last_run_duration**|**int**|Продолжительность последнего выполнения задания на целевом сервере.|  
|**last_run_outcome**|**tinyint**|Результат последнего выполнения задания на данном сервере:<br /><br /> **0** = сбой<br /><br /> **1** = успех<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_outcome_message**|**nvarchar(1024)**|Сообщение о результате последнего выполнения задания на данном целевом сервере.|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены **SQLAgentUserRole** могут только просматривать задания, которыми они владеют. Члены **sysadmin**, **SQLAgentReaderRole**и **SQLAgentOperatorRole** могут просматривать все локальные и многосерверные задания.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-list-information-for-all-jobs"></a>A. Вывод списка сведений обо всех заданиях  
 На следующем примере показано, как процедура `sp_help_job`, выполняемая без параметров, возвращает сведения обо всех заданиях, определенных в данный момент в базе данных `msdb`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-matching-a-specific-criteria"></a>Б. Вывод сведений о заданиях, совпадающих с определенным критерием  
 В следующем примере показано, как выводятся сведения о многосерверных заданиях, владельцем которых является `françoisa`, которые включены и выполняются.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job   
   @job_type = N'MULTI-SERVER',  
   @owner_login_name = N'françoisa',  
   @enabled = 1,  
   @execution_status = 1 ;  
GO  
```  
  
### <a name="c-listing-all-aspects-of-information-for-a-job"></a>В. Вывод всех аспектов сведений о задании  
 На следующем примере показано, как выводится список всех аспектов сведений о задании `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job  
    @job_name = N'NightlyBackups',  
    @job_aspect = N'ALL' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
