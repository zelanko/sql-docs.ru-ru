---
description: sp_delete_job (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f11bf53f9663893c2d678e7a7af904b70b4fc1cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493351"
---
# <a name="sp_delete_job-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @job_id = ] job_id` Идентификационный номер удаляемого задания. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` Имя удаляемого задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name*. нельзя указывать оба значения.  
  
`[ @originating_server = ] 'server'` Для внутреннего использования.  
  
`[ @delete_history = ] delete_history` Указывает, следует ли удалить журнал задания. *delete_history* имеет **бит**и значение по умолчанию **1**. Если *delete_history* равен **1**, журнал заданий для задания удаляется. Если значение *delete_history* равно **0**, журнал заданий не удаляется.  
  
 Обратите внимание, что при удалении задания, если журнал не удаляется, исторические данные для задания не будут отображаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнале заданий графического пользовательского интерфейса агента, но информация по-прежнему будет находиться в таблице **sysjobhistory** базы данных **msdb** .  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` Указывает, следует ли удалять расписания, присоединенные к этому заданию, если они не присоединены к другим заданиям. *delete_unused_schedule* имеет **бит**и значение по умолчанию **1**. Если *delete_unused_schedule* равен **1**, то расписания, прикрепленные к этому заданию, удаляются, если другие задания не ссылаются на расписание. Если *delete_unused_schedule* равен **0**, расписания не удаляются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Аргумент ** \@ originating_server** зарезервирован для внутреннего использования.  
  
 Аргумент ** \@ delete_unused_schedule** обеспечивает обратную совместимость с предыдущими версиями SQL Server путем автоматического удаления расписаний, не присоединенных к какому бы то ни было заданию. Обратите внимание, что поведение этого параметра по умолчанию обеспечивает обратную совместимость. Чтобы хранить расписания, которые не присоединены к заданию, необходимо указать значение **0** в качестве аргумента ** \@ delete_unused_schedule** .  
  
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
  
## <a name="see-also"></a>См. также:  
 [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
