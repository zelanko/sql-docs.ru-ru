---
description: sp_add_job (Transact-SQL)
title: sp_add_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 89f90d460287fadc9cdda97c020ccef7a47ceccd
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753867"
---
# <a name="sp_add_job-transact-sql"></a>sp_add_job (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Добавляет новое задание, выполняемое службой агента SQL Server.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
 > [!IMPORTANT]  
 > В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).
 
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
`[ @job_name = ] 'job_name'` Имя задания. Имя должно быть уникальным и не может содержать символ процента ( **%** ). *job_name*имеет тип **nvarchar (128)** и не имеет значения по умолчанию.  
  
`[ @enabled = ] enabled` Указывает состояние добавленного задания. *Enabled*имеет тип **tinyint**и значение по умолчанию 1 (включено). Если значение **равно 0**, задание не включено и не выполняется в соответствии с расписанием. Однако его можно запустить вручную.  
  
`[ @description = ] 'description'` Описание задания. *Description* имеет тип **nvarchar (512)** и значение по умолчанию NULL. Если *Описание* отсутствует, используется параметр "нет описания".  
  
`[ @start_step_id = ] step_id` Идентификационный номер первого шага, выполняемого для задания. *step_id*имеет **тип int**и значение по умолчанию 1.  
  
`[ @category_name = ] 'category'` Категория для задания. *Category*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @category_id = ] category_id` Независимый от языка механизм для указания категории заданий. *category_id*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @owner_login_name = ] 'login'` Имя входа, владеющего заданием. Аргумент *Login*имеет тип **sysname**и значение по умолчанию NULL, которое интерпретируется как текущее имя входа. Только члены предопределенной роли сервера **sysadmin** могут устанавливать или изменять значение для ** \@ owner_login_name**. Если пользователи, не являющиеся участниками роли **sysadmin** , или изменяют значение ** \@ owner_login_name**, выполнение этой хранимой процедуры завершается неудачей и возвращается ошибка.  
  
`[ @notify_level_eventlog = ] eventlog_level` Значение, указывающее, когда следует поместить запись в журнал приложений Microsoft Windows для этого задания. *eventlog_level*имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Никогда|  
|**1**|При успешном завершении|  
|**2** (по умолчанию)|При сбое|  
|**3**|Всегда|  
  
`[ @notify_level_email = ] email_level` Значение, указывающее, когда следует отправить сообщение электронной почты после завершения этого задания. *email_level*имеет **тип int**и значение по умолчанию **0**, что означает Never. *email_level*использует те же значения, что и *eventlog_level*.  
  
`[ @notify_level_netsend = ] netsend_level` Значение, указывающее, когда следует отправить сетевое сообщение после завершения этого задания. *netsend_level*имеет **тип int**и значение по умолчанию **0**, что означает Never. *netsend_level* использует те же значения, что и *eventlog_level*.  
  
`[ @notify_level_page = ] page_level` Значение, указывающее, когда следует отправить страницу после завершения этого задания. *page_level*имеет **тип int**и значение по умолчанию **0**, что означает Never. *page_level*использует те же значения, что и *eventlog_level*.  
  
`[ @notify_email_operator_name = ] 'email_name'` Адрес электронной почты пользователя, которому отправляется сообщение при достижении *email_level* . Аргумент *email_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @notify_netsend_operator_name = ] 'netsend_name'` Имя оператора, которому отправляется сетевое сообщение после завершения этого задания. Аргумент *netsend_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @notify_page_operator_name = ] 'page_name'` Имя пользователя, которому будет присвоена страница после завершения этого задания. Аргумент *page_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @delete_level = ] delete_level` Значение, указывающее, когда следует удалять задание. *delete_value*имеет **тип int**и значение по умолчанию 0, что означает никогда. *delete_level*использует те же значения, что и *eventlog_level*.  
  
> [!NOTE]  
>  Если *delete_level* имеет значение **3**, задание выполняется только один раз, независимо от всех расписаний, определенных для задания. Если в какой-то момент задание удаляет себя, журнал этого задания также удаляется.  
  
`[ @job_id = ] _job_idOUTPUT` Идентификационный номер задания, назначенный заданию при успешном создании. *job_id*является выходной переменной типа **uniqueidentifier**и ЗНАЧЕНИЕМ по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 ** \@ originating_server** существует в **sp_add_job,** но не указана в списке arguments. ** \@ originating_server** зарезервировано для внутреннего использования.  
  
 После выполнения **sp_add_job** для добавления задания **sp_add_jobstep** можно использовать для добавления действий, выполняющих действия для задания. **sp_add_jobschedule** можно использовать для создания расписания, используемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службой агента для выполнения задания. Используйте **sp_add_jobserver** , чтобы задать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр, в котором выполняется задание, и **sp_delete_jobserver** , чтобы удалить задание из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
 Если задание будет выполняться на одном или нескольких целевых серверах в многосерверной среде, используйте **sp_apply_job_to_targets** , чтобы задать целевые серверы или группы целевых серверов для задания. Чтобы удалить задания с целевых серверов или групп целевых серверов, используйте **sp_remove_job_from_targets**.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователи должны быть членами предопределенной роли сервера **sysadmin** или иметь одну из следующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предопределенных ролей базы данных агента, которая находится в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Сведения о конкретных разрешениях, связанных с каждой из этих предопределенных ролей базы данных, см. в разделе агент SQL Server предопределенных [ролей базы данных](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены предопределенной роли сервера **sysadmin** могут устанавливать или изменять значение для ** \@ owner_login_name**. Если пользователи, не являющиеся участниками роли **sysadmin** , или изменяют значение ** \@ owner_login_name**, выполнение этой хранимой процедуры завершается неудачей и возвращается ошибка.  
  
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
  
