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
ms.openlocfilehash: fc733ca2b56ef9fa96be5ab2adf6486419e0e250
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306272"
---
# <a name="sp_delete_job-transact-sql"></a>sp_delete_job (Transact-SQL)
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
`[ @job_id = ] job_id` — идентификационный номер удаляемого задания. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` — имя удаляемого задания. Аргумент *имя_задания* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать *job_id* или *имя_задания*. нельзя указывать оба значения.  
  
`[ @originating_server = ] 'server'` для внутреннего использования.  
  
`[ @delete_history = ] delete_history` указывает, следует ли удалить журнал задания. *delete_history* имеет **бит**и значение по умолчанию **1**. Если *delete_history* имеет значение **1**, журнал заданий для задания удаляется. Если *delete_history* имеет значение **0**, журнал заданий не удаляется.  
  
 Обратите внимание, что при удалении задания, если журнал не удаляется, исторические данные для задания не отображаются в журнале заданий графического пользовательского интерфейса агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но информация по-прежнему будет находиться в таблице **sysjobhistory** в **базе данных msdb.** база данных.  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` указывает, следует ли удалять расписания, присоединенные к этому заданию, если они не присоединены к другим заданиям. *delete_unused_schedule* имеет **бит**и значение по умолчанию **1**. Если *delete_unused_schedule* имеет значение **1**, то расписания, прикрепленные к этому заданию, удаляются, если другие задания не ссылаются на расписание. Если *delete_unused_schedule* имеет значение **0**, расписания не удаляются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Аргумент **\@originating_server** зарезервирован для внутреннего использования.  
  
 Аргумент **\@delete_unused_schedule** обеспечивает обратную совместимость с предыдущими версиями SQL Server путем автоматического удаления расписаний, не присоединенных к какому-либо заданию. Обратите внимание, что поведение этого параметра по умолчанию обеспечивает обратную совместимость. Чтобы хранить расписания, которые не присоединены к заданию, необходимо указать значение **0** в качестве аргумента **\@delete_unused_schedule** .  
  
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
  
  
