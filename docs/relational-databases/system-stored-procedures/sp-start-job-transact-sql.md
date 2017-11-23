---
title: "sp_start_job (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_start_job
- sp_start_job_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_start_job
ms.assetid: 8a91df6a-eb84-4512-9a17-4a6e32a9538a
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 628484b1f5e2bf4282eb4f4b223beba5636d4ba5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spstartjob-transact-sql"></a>sp_start_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отдает агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распоряжение немедленно выполнить задание.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
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
 [  **@job_name=** ] **"***job_name***"**  
 Имя запускаемого задания. Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно. *job_name* — **sysname**, значение по умолчанию NULL.  
  
 [  **@job_id=** ] *job_id*  
 Идентификационный номер запускаемого задания. Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@error_flag=** ] *error_flag*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@server_name=** ] **"***имя_сервера***"**  
 Имя целевого сервера, на котором запускается задание. *имя_сервера* — **nvarchar(128)**, значение по умолчанию NULL. *имя_сервера* должен быть один из целевых серверов, к которым в настоящее время нацелено задания.  
  
 [  **@step_name=** ] **"***step_name***"**  
 Имя этапа, с которого начинается выполнение задания. Применяется только к локальным заданиям. *step_name* — **sysname**, значение по умолчанию NULL  
  
 [  **@output_flag=** ] *output_flag*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Эта хранимая процедура находится в **msdb** базы данных.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** и **SQLAgentReaderRole** можно запускать только задания, которыми они владеют. Члены **SQLAgentOperatorRole** можно запускать все локальные задания, включая те, которыми владеют другие пользователи. Члены **sysadmin** доступен запуск всех локальных и многосерверных заданий.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как запускается задание с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_stop_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
