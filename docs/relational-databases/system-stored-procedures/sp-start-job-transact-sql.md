---
title: sp_start_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_start_job
- sp_start_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_start_job
ms.assetid: 8a91df6a-eb84-4512-9a17-4a6e32a9538a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85878b79ec98b3523f18ed1c5c4d3f1bf08fc540
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526676"
---
# <a name="spstartjob-transact-sql"></a>sp_start_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отдает агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распоряжение немедленно выполнить задание.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_start_job   
     {   [@job_name =] 'job_name'  
       | [@job_id =] job_id }  
     [ , [@error_flag =] error_flag]  
     [ , [@server_name =] 'server_name']  
     [ , [@step_name =] 'step_name']  
     [ , [@output_flag =] output_flag]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_name = ] 'job_name'` Имя задания. Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно. *имя_задания* — **sysname**, значение по умолчанию NULL.  
  
`[ @job_id = ] job_id` Идентификационный номер задания. Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно. *job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
`[ @error_flag = ] error_flag` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @server_name = ] 'server_name'` Целевой сервер, на котором для запуска задания. *имя_сервера* — **nvarchar(128)**, значение по умолчанию NULL. *имя_сервера* должен быть одним из целевых серверов, на которых задание в настоящее время нацелено.  
  
`[ @step_name = ] 'step_name'` Имя этапа, с которого начинается выполнение задания. Применяется только к локальным заданиям. *step_name* — **sysname**, значение по умолчанию NULL  
  
`[ @output_flag = ] output_flag` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Эта хранимая процедура находится в **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Членами **SQLAgentUserRole** и **SQLAgentReaderRole** можно запускать только задания, которыми они владеют. Членами **SQLAgentOperatorRole** можно запускать все локальные задания, включая те, которыми владеют другие пользователи. Членами **sysadmin** доступен запуск всех локальных и многосерверных заданий.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как запускается задание с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
