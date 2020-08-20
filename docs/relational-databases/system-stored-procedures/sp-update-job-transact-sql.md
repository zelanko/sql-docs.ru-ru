---
description: sp_update_job (Transact-SQL)
title: sp_update_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 88123b9997d1111c0254d38fd770bb1fd8949d0e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485595"
---
# <a name="sp_update_job-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет атрибуты задания.  
  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id` Идентификационный номер обновляемого задания. *job_id*имеет тип **uniqueidentifier**.  
  
`[ @job_name = ] 'job_name'` Имя задания. *job_name* имеет тип **nvarchar (128)**.  
  
> **Примечание.** Необходимо указать либо *job_id* , либо *job_name* , но не указывать оба значения.  
  
`[ @new_name = ] 'new_name'` Новое имя для задания. *new_name* имеет тип **nvarchar (128)**.  
  
`[ @enabled = ] enabled` Указывает, включено ли задание (**1**) или не включено (**0**). *Enabled* имеет тип **tinyint**.  
  
`[ @description = ] 'description'` Описание задания. *Описание* — **nvarchar (512)**.  
  
`[ @start_step_id = ] step_id` Идентификационный номер первого шага, выполняемого для задания. *step_id* имеет **тип int**.  
  
`[ @category_name = ] 'category'` Категория задания. *Category имеет тип* **nvarchar (128)**.  
  
`[ @owner_login_name = ] 'login'` Имя входа, владеющего заданием. *имя для входа* — **nvarchar (128)** . только члены предопределенной роли сервера **sysadmin** могут изменять владельца задания.  
  
`[ @notify_level_eventlog = ] eventlog_level` Указывает, когда следует поместить запись в журнал приложений Microsoft Windows для этого задания. *eventlog_level*имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**0**|Никогда|  
|**1**|При успешном завершении|  
|**2**|При сбое|  
|**3**|Всегда|  
  
`[ @notify_level_email = ] email_level` Указывает, когда следует отправить сообщение по электронной почте после завершения этого задания. *email_level*имеет **тип int**. *email_level*использует те же значения, что и *eventlog_level*.  
  
`[ @notify_level_netsend = ] netsend_level` Указывает, когда следует отправить сетевое сообщение после завершения этого задания. *netsend_level*имеет **тип int**. *netsend_level*использует те же значения, что и *eventlog_level*.  
  
`[ @notify_level_page = ] page_level` Указывает, когда следует отправить страницу после завершения этого задания. *page_level* имеет **тип int**. *page_level*использует те же значения, что и *eventlog_level*.  
  
`[ @notify_email_operator_name = ] 'operator_name'` Имя оператора, которому отправляется сообщение электронной почты при достижении *email_level* . *email_name* имеет тип **nvarchar (128)**.  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` Имя оператора, которому отправляется сетевое сообщение. *netsend_operator* имеет тип **nvarchar (128)**.  
  
`[ @notify_page_operator_name = ] 'page_operator'` Имя оператора, которому отправляется страница. *page_operator* имеет тип **nvarchar (128)**.  
  
`[ @delete_level = ] delete_level` Указывает, когда следует удалять задание. *delete_value*имеет **тип int**. *delete_level*использует те же значения, что и *eventlog_level*.  
  
`[ @automatic_post = ] automatic_post` Процессу.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_update_job** должны запускаться из базы данных **msdb** .  
  
 **sp_update_job** изменяет только те параметры, для которых указаны значения параметров. Если параметр пропущен, сохраняется текущая настройка.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **роли sysadmin** могут использовать эту хранимую процедуру для изменения атрибутов заданий, принадлежащих другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяются имя, описание и включенное состояние задания `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
