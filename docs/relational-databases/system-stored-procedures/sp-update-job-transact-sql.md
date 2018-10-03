---
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4371609b9d0c72d9d589d37f0edacc4d37a2996c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651562"
---
# <a name="spupdatejob-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@job_id =**] *job_id*  
 Идентификатор обновляемого задания. *job_id*— **uniqueidentifier**.  
  
 [  **@job_name =**] **"***имя_задания***"**  
 Имя задания. *имя_задания*— **nvarchar(128)**.  
  
> **Примечание:** либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@new_name =**] **"***новое_имя***"**  
 Новое имя задания. *новое_имя*— **nvarchar(128)**.  
  
 [  **@enabled =**] *включена*  
 Указывает, включено ли задание (**1**) или не включено (**0**). *включить*— **tinyint**.  
  
 [  **@description =**] **"***описание***"**  
 Описание задания. *Описание* — **nvarchar(512)**.  
  
 [  **@start_step_id =**] *step_id*  
 Идентификатор первого этапа, выполняемого в ходе задания. *step_id*— **int**.  
  
 [  **@category_name =**] **"***категории***"**  
 Категория задания. *Категория*— **nvarchar(128)**.  
  
 [  **@owner_login_name =**] **"***входа***"**  
 Имя входа, которое владеет заданием. *Имя входа*— **nvarchar(128)** только членами **sysadmin** предопределенной роли сервера можно изменить владельца задания.  
  
 [ **@notify_level_eventlog =**] *eventlog_level*  
 Указывает, следует ли помещать запись в журнал приложений Microsoft Windows для данного задания. *eventlog_level*— **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**0**|Никогда|  
|**1**|При успешном завершении|  
|**2**|При сбое|  
|**3**|Всегда|  
  
 [ **@notify_level_email =**] *email_level*  
 Указывает, нужно ли отправить сообщение электронной почты по завершении этого задания. *email_level*— **int**. *email_level*использует те же значения, что *eventlog_level*.  
  
 [ **@notify_level_netsend =**] *netsend_level*  
 Указывает, нужно ли отправить сетевое сообщение по завершении этого задания. *netsend_level*— **int**. *netsend_level*использует те же значения, что *eventlog_level*.  
  
 [ **@notify_level_page =**] *page_level*  
 Указывает, необходимо ли отправить страницу по завершении этого задания. *page_level*— **int**. *page_level*использует те же значения, что *eventlog_level*.  
  
 [  **@notify_email_operator_name =**] **"***имя_оператора***"**  
 Имя оператора, которому отправляется сообщение электронной почты при *email_level* достижения. *имя_электронной_почты* — **nvarchar(128)**.  
  
 [  **@notify_netsend_operator_name =**] **"***netsend_operator***"**  
 Имя оператора, которому отправляется сетевое сообщение. *netsend_operator* — **nvarchar(128)**.  
  
 [  **@notify_page_operator_name =**] **"***page_operator***"**  
 Имя оператора, которому отправляется страница. *page_operator* — **nvarchar(128)**.  
  
 [ **@delete_level =**] *delete_level*  
 Указывает, когда необходимо удалить задание. *delete_value*— **int**. *delete_level*использует те же значения, что *eventlog_level*.  
  
 [  **@automatic_post =**] *automatic_post*  
 Зарезервировано.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_update_job** должна запускаться из **msdb** базы данных.  
  
 **sp_update_job** изменяет только те установки, о параметрах которого предоставляются значения. Если параметр пропущен, сохраняется текущая настройка.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **sysadmin** можно использовать эту хранимую процедуру для редактирования атрибутов заданий, принадлежащие другим пользователям.  
  
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
  
## <a name="see-also"></a>См. также  
 [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
