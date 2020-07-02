---
title: sp_remove_job_from_targets (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 033a2c950ec695a64aced30a383d25206e7f6d10
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751679"
---
# <a name="sp_remove_job_from_targets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Удаляет указанное задание из данных целевых серверов или групп целевых серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификационный номер задания, из которого удаляются указанные целевые серверы или группы целевых серверов. Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания, из которого необходимо удалить указанные целевые серверы или группы целевых серверов. Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @target_server_groups = ] 'target_server_groups'`Разделенный запятыми список групп целевых серверов, которые будут удалены из указанного задания. *target_server_groups* имеет тип **nvarchar (1024)** и значение по умолчанию NULL.  
  
`[ @target_servers = ] 'target_servers'`Разделенный запятыми список целевых серверов, которые будут удалены из указанного задания. *target_servers* имеет тип **nvarchar (1024)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется ранее созданное задание `Weekly Sales Backups` из группы целевых серверов `Servers Processing Customer Orders` и из серверов `SEATTLE1` и `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
