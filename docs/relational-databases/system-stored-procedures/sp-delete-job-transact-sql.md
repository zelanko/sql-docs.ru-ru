---
title: sp_delete_job (Transact-SQL) | Документы Microsoft
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
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c578243ec78605216a3cb5c640e6779e712fec46
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 [  **@job_id=** ] *job_id*  
 Идентификатор удаляемого задания. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name=** ] **"***job_name***"**  
 Имя удаляемого задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name*должно быть указано; невозможно указать одновременно.  
  
 [ **@originating_server=** ] **'***server***'**  
 Для внутреннего использования.  
  
 [  **@delete_history=** ] *delete_history*  
 Указывает, следует ли удалить журнал задания. *delete_history* — **бит**, значение по умолчанию **1**. Когда *delete_history* — **1**, журнала заданий для задания удаляются. Когда *delete_history* — **0**, журнал заданий не удаляется.  
  
 Обратите внимание, что если задание удалено, данные журнала не удаляются данные предыстории для задания не будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнал заданий агента графический пользовательский интерфейс, но эти данные по-прежнему будет находиться в **sysjobhistory**в таблицу **msdb** базы данных.  
  
 [ **@delete_unused_schedule=** ] *delete_unused_schedule*  
 Указывает, следует ли удалить расписания, связанные с этим заданием, если они не связаны ни с одним другим заданием. *delete_unused_schedule* — **бит**, значение по умолчанию **1**. Когда *delete_unused_schedule* — **1**, расписания, связанные с этим заданием, удаляются, если больше ни одно задание ссылаются на расписание. Когда *delete_unused_schedule* — **0**, расписания, не удаляются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **@originating_server** Аргумент зарезервирован для внутреннего использования.  
  
 **@delete_unused_schedule** Аргумент обеспечивает обратную совместимость с предыдущими версиями SQL Server путем автоматического удаления расписаний, не присоединенные к любое задание. Обратите внимание, что поведение этого параметра по умолчанию обеспечивает обратную совместимость. Чтобы сохранить расписания, не прикреплено к заданию, необходимо задать значение **0** как **@delete_unused_schedule** аргумент.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
 С помощью этой хранимой процедуры нельзя удалить планы обслуживания и задания, которые являются частью планов обслуживания. Для удаления планов обслуживания следует использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
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
  
  
