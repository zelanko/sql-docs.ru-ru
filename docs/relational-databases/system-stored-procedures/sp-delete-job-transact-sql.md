---
title: sp_delete_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 94b77b30d96b5361967398a35335f6aa96587f1b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085331"
---
# <a name="spdeletejob-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет задание.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_job { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
     [ , [ @originating_server = ] 'server' ]   
     [ , [ @delete_history = ] delete_history ]  
     [ , [ @delete_unused_schedule = ] delete_unused_schedule ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id` — Это идентификационный номер задания для удаления. *job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` — Имя задания для удаления. *имя_задания* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания*должен быть указан, нельзя указать одновременно.  
  
`[ @originating_server = ] 'server'` Для внутреннего использования.  
  
`[ @delete_history = ] delete_history` Указывает, следует ли удалить журнал задания. *delete_history* — **бит**, значение по умолчанию **1**. Когда *delete_history* — **1**, удаляется журнал заданий для задания. Когда *delete_history* — **0**, журнал заданий не удаляется.  
  
 Обратите внимание, что когда задание удалено, а журнал не удаляется, исторические сведения для задания не будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнал заданий агента графический пользовательский интерфейс, но эти данные по-прежнему будет находиться в **sysjobhistory**в таблицу **msdb** базы данных.  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` Указывает, является ли удалить расписания связанные с этим заданием, если они не присоединены к любых других заданий. *delete_unused_schedule* — **бит**, значение по умолчанию **1**. Когда *delete_unused_schedule* — **1**, расписания, связанные с этим заданием, удаляются, если нет других заданий ссылаются на расписание. Когда *delete_unused_schedule* — **0**, расписания не удаляются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **@originating_server** Аргумент зарезервирован для внутреннего использования.  
  
 **@delete_unused_schedule** Аргумент обеспечивает обратную совместимость с предыдущими версиями SQL Server путем автоматического удаления расписаний, не вложенные в любое задание. Обратите внимание, что поведение этого параметра по умолчанию обеспечивает обратную совместимость. Чтобы сохранить расписания, которые не присоединены к заданию, необходимо указать значение **0** как **@delete_unused_schedule** аргумент.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
 С помощью этой хранимой процедуры нельзя удалить планы обслуживания и задания, которые являются частью планов обслуживания. Для удаления планов обслуживания следует использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены предопределенной роли сервера **sysadmin** с помощью процедуры **sp_delete_job** могут удалить любое задание. Пользователь, который не является членом предопределенной роли сервера **sysadmin** , может удалять только задания, принадлежащие этому пользователю.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется задание `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
