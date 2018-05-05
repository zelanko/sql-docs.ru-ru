---
title: sp_remove_job_from_targets (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4449e4879254f183329f6df0040687ca69981669
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spremovejobfromtargets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [  **@job_id =**] *job_id*  
 Идентификационный номер задания, из которого следует удалить указанные целевые серверы и группы целевых серверов. Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name =**] **"***job_name***"**  
 Имя указания, из которого следует удалить указанные целевые серверы и группы целевых серверов. Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно. *job_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@target_server_groups =**] **'***target_server_groups***'**  
 Список разделенных запятыми групп целевых серверов, которые следует удалить из указанного задания. *target_server_groups* — **nvarchar(1024)**, значение по умолчанию NULL.  
  
 [ **@target_servers =**] **'***target_servers***'**  
 Список разделенных запятыми целевых серверов, которые следует удалить из указанного задания. *target_servers* — **nvarchar(1024)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
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
  
  
