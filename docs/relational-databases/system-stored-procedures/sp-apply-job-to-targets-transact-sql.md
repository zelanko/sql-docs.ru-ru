---
title: sp_apply_job_to_targets (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f293e906d647d318bca5d730d0164b75cc88fc6f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998028"
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Применяет задание к одному или нескольким целевым серверам или к целевым серверам, принадлежащим к одной или нескольким группам целевых серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id` Идентификационный номер задания, применяемого к указанным целевым серверам или группам целевых серверов. *job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` Имя задания, применяемого к указанным целевым серверам или группам целевых серверов. *имя_задания* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
`[ @target_server_groups = ] 'target_server_groups'` Список разделенных запятыми групп целевых серверов, на которые имеет указанное задание, для применения. *target_server_groups* — **nvarchar(2048)**, значение по умолчанию NULL.  
  
`[ @target_servers = ] 'target_servers'` Разделенный запятыми список целевых серверов, на которые имеет указанное задание, для применения. *target_servers*— **nvarchar(2048)**, значение по умолчанию NULL.  
  
`[ @operation = ] 'operation'` Является ли указанное задание следует применить к или удалено с указанных целевых серверов или групп целевых серверов. *Операция*— **varchar(7)**, значение по умолчанию APPLY. Допустимы следующие операции: **применить** и **удалить**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_apply_job_to_targets** предоставляет простой способ для применения (или удаления) задания к нескольким целевым серверам и является альтернативой вызову **sp_add_jobserver** (или **sp_delete_jobserver**) один раз для каждого целевого сервера требуется.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнить эту процедуру.  
  
## <a name="examples"></a>Примеры  
 В следующем примере ко всем целевым серверам в группе `Backup Customer Information` применяется ранее созданное задание `Servers Maintaining Customer Information`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
