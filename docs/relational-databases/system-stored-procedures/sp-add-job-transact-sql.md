---
title: sp_add_job (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a71f128947a3e8acc08760ed19c31af949210384
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddjob-transact-sql"></a>sp_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новое задание, выполняемое службой SQLServerAgent.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_job [ @job_name = ] 'job_name'  
     [ , [ @enabled = ] enabled ]   
     [ , [ @description = ] 'description' ]   
     [ , [ @start_step_id = ] step_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @category_id = ] category_id ]   
     [ , [ @owner_login_name = ] 'login' ]   
     [ , [ @notify_level_eventlog = ] eventlog_level ]   
     [ , [ @notify_level_email = ] email_level ]   
     [ , [ @notify_level_netsend = ] netsend_level ]   
     [ , [ @notify_level_page = ] page_level ]   
     [ , [ @notify_email_operator_name = ] 'email_name' ]   
          [ , [ @notify_netsend_operator_name = ] 'netsend_name' ]   
     [ , [ @notify_page_operator_name = ] 'page_name' ]   
     [ , [ @delete_level = ] delete_level ]   
     [ , [ @job_id = ] job_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_name =** ] **"***job_name***"**  
 Имя задания. Имя должно быть уникальным и не может содержать символа процента (**%**) символов. *job_name*— **nvarchar(128)**, не имеет значения по умолчанию.  
  
 [  **@enabled =** ] *включена*  
 Отображает состояние добавленного задания. *включить*— **tinyint**, значение по умолчанию 1 (включено). Если **0**, задание отключено и не запускается согласно расписанию, однако ее можно запустить вручную.  
  
 [  **@description =** ] **"***описание***"**  
 Описание задания. *Описание* — **nvarchar(512)**, значение по умолчанию NULL. Если *описание* — этот параметр опущен, используется «Описание недоступно».  
  
 [  **@start_step_id =** ] *step_id*  
 Идентификатор первого этапа, выполняемого в ходе задания. *step_id*— **int**, значение по умолчанию 1.  
  
 [  **@category_name =** ] **"***категории***"**  
 Категория задания. *Категория*— **sysname**, значение по умолчанию NULL.  
  
 [  **@category_id =** ] *category_id*  
 Независимый от языка механизм указания категории задания. *category_id*— **int**, значение по умолчанию NULL.  
  
 [  **@owner_login_name =** ] **"***входа***"**  
 Имя входа, которое владеет заданием. *Имя входа*— **sysname**, значение по умолчанию NULL, которое интерпретируется как текущее имя входа. Только члены **sysadmin** предопределенной роли сервера можно задать или изменить значение для **@owner_login_name**. Если пользователи, не являющиеся членами из **sysadmin** роли задать или изменить значение **@owner_login_name**, происходит сбой выполнения этой хранимой процедуры, и возвращается сообщение об ошибке.  
  
 [ **@notify_level_eventlog =** ] *eventlog_level*  
 Значение, указывающее, когда следует помещать запись в журнал приложений Microsoft Windows для данного задания. *eventlog_level*— **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Никогда|  
|**1**|При успешном завершении|  
|**2** (по умолчанию)|При сбое|  
|**3**|Всегда|  
  
 [  **@notify_level_email =** ] *email_level*  
 Значение, указывающее, нужно ли отправить сообщение электронной почты по завершении этого задания. *email_level*— **int**, значение по умолчанию **0**, не отправлять никогда. *email_level*использует те же значения, как *eventlog_level*.  
  
 [  **@notify_level_netsend =** ] *netsend_level*  
 Значение, указывающее, нужно ли отправить сетевое сообщение по завершении этого задания. *netsend_level*— **int**, значение по умолчанию **0**, не отправлять никогда. *netsend_level* использует те же значения, как *eventlog_level*.  
  
 [  **@notify_level_page =** ] *page_level*  
 Значение, указывающее, нужно ли отправить сообщение на пейджер по завершении этого задания. *page_level*— **int**, значение по умолчанию **0**, не отправлять никогда. *page_level*использует те же значения, как *eventlog_level*.  
  
 [  **@notify_email_operator_name =** ] **"***имя_электронной_почты***"**  
 Имя электронной почты лица, которому отправляется по электронной почте при *email_level* достигается. *имя_электронной_почты* — **sysname**, значение по умолчанию NULL.  
  
 [  **@notify_netsend_operator_name =** ] **"***netsend_name***"**  
 Имя оператора, которому отправляется сетевое сообщение после выполнения данного задания. *netsend_name*— **sysname**, значение по умолчанию NULL.  
  
 [  **@notify_page_operator_name =** ] **"***page_name***"**  
 Имя лица, которое уведомляется по пейджеру о выполнении данного задания. *page_name*— **sysname**, значение по умолчанию NULL.  
  
 [ **@delete_level =** ] *delete_level*  
 Значение, указывающее, нужно ли удалять задание. *delete_value*— **int**, значение по умолчанию 0, означающее никогда. *delete_level*использует те же значения, как *eventlog_level*.  
  
> [!NOTE]  
>  Когда *delete_level* — **3**, задание выполняется только один раз, независимо от того, все расписания определенные для задания. Если в какой-то момент задание удаляет себя, журнал этого задания также удаляется.  
  
 [  **@job_id =** ] *job_id *** выходных данных**  
 Идентификационный номер задания, присваиваемый заданию после успешного создания. *Аргумент job_id*является выходной переменной типа **uniqueidentifier**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **@originating_server** существует в **sp_add_job** , но отсутствует в списке аргументов. **@originating_server** Зарезервировано для внутреннего использования.  
  
 После **sp_add_job** был выполнен для добавления задания **sp_add_jobstep** можно использовать для добавления шагов, выполняющих действия задания. **sp_add_jobschedule** можно использовать для создания расписания, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службой агента для выполнения задания. Используйте **sp_add_jobserver** для задания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр, на котором выполняется задание, и **sp_delete_jobserver** для удаления задания из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
 Если задание должно выполняться на целевых серверах в многосерверной среде, используйте **sp_apply_job_to_targets** определения целевых серверов или групп целевых серверов задания. Для удаления заданий с целевых серверов или групп целевых серверов используется **sp_remove_job_from_targets**.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователи должны входить в **sysadmin** предопределенной роли сервера или быть предоставлена одна из следующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предопределенных ролей базы данных, которые находятся в агента **msdb** базы данных:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о конкретных разрешениях, связанных с каждой из этих предопределенных ролей базы данных см. в разделе [SQL Server предопределенных ролей базы данных агента](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** предопределенной роли сервера можно задать или изменить значение для **@owner_login_name**. Если пользователи, не являющиеся членами из **sysadmin** роли задать или изменить значение **@owner_login_name**, происходит сбой выполнения этой хранимой процедуры, и возвращается сообщение об ошибке.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-job"></a>A. Создание задания  
 В этом примере создается новое задание с именем `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-adding-a-job-with-pager-e-mail-and-net-send-information"></a>Б. Создание задания с уведомлением по пейджеру, электронной почте и по сети  
 Этот пример иллюстрирует создание задания `Ad hoc Sales Data Backup`, в случае сбоя которого пользователь `François Ajenstat` получает уведомление (по пейджеру, электронной почте или с помощью сетевого всплывающего сообщения); в случае успешного завершения задания выполняется его удаление.  
  
> [!NOTE]  
>  В данном примере предполагается, что оператор с именем `François Ajenstat` и имя входа `françoisa` уже существуют.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'Ad hoc Sales Data Backup',   
    @enabled = 1,  
    @description = N'Ad hoc backup of sales data',  
    @owner_login_name = N'françoisa',  
    @notify_level_eventlog = 2,  
    @notify_level_email = 2,  
    @notify_level_netsend = 2,  
    @notify_level_page = 2,  
    @notify_email_operator_name = N'François Ajenstat',  
    @notify_netsend_operator_name = N'François Ajenstat',   
    @notify_page_operator_name = N'François Ajenstat',  
    @delete_level = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
