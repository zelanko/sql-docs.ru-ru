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
ms.openlocfilehash: 1b3015651dc263d95aa80e6108db2e8017e112d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032830"
---
# <a name="sp_start_job-transact-sql"></a>sp_start_job (Transact-SQL)
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
`[ @job_name = ] 'job_name'`Имя запускаемого задания. Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @job_id = ] job_id`Идентификационный номер запускаемого задания. Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @error_flag = ] error_flag` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @server_name = ] 'server_name'`Целевой сервер, на котором необходимо запустить задание. *server_name* имеет тип **nvarchar (128)** и значение по умолчанию NULL. *server_name* должен быть одним из целевых серверов, на которые в данный момент нацелено задание.  
  
`[ @step_name = ] 'step_name'`Имя шага, с которого начинается выполнение задания. Применяется только к локальным заданиям. Аргумент *step_name* имеет тип **sysname**и значение по умолчанию NULL  
  
`[ @output_flag = ] output_flag` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Эта хранимая процедура находится в базе данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены ролей **SQLAgentUserRole** и **SQLAgentReaderRole** могут запускать только те задания, которыми они владеют. Члены **SQLAgentOperatorRole** могут запускать все локальные задания, включая те, которые принадлежат другим пользователям. Члены **роли sysadmin** могут запускать все локальные и многосерверные задания.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как запускается задание с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
