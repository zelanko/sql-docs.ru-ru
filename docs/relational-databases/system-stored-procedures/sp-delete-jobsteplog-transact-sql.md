---
title: sp_delete_jobsteplog (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
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
- sp_delete_jobsteplog
- sp_delete_jobsteplog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobsteplog
ms.assetid: e9ef4c99-abde-4038-b6a3-a25dcbaf0958
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 99f60818976dc3c89e11d2fd1256a7aecd7d8b63
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdeletejobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет все журналы шагов заданий для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], заданные аргументами. Используйте эту хранимую процедуру для поддержания **sysjobstepslogs** в таблицу **msdb** базы данных.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@job_id =**] **'***job_id***'**  
 Идентификационный номер задания, содержащего журнал шагов задания, который необходимо удалить. *Аргумент job_id* — **int**, значение по умолчанию NULL.  
  
 [  **@job_name =**] **"***job_name***"**  
 Имя задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> **Примечание:** либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@step_id =**] *step_id*  
 Идентификационный номер шага задания, журнал которого планируется удалить. Если не включен, удаляются все журналы шагов задания, если **@older_than** или **@larger_than** указаны. *step_id* — **int**, значение по умолчанию NULL.  
  
 [  **@step_name =**] **"***step_name***"**  
 Имя шага задания, журнал которого необходимо удалить. *step_name* — **sysname**, значение по умолчанию NULL.  
  
> **Примечание:** либо *step_id* или *step_name* можно указать, но не оба аргумента одновременно.  
  
 [  **@older_than =**] **"***даты***"**  
 Дата и время создания старейшего сохраняемого журнала шагов задания. Удаляются все журналы шагов задания старше указанной даты и времени. *Дата* — **datetime**, значение по умолчанию NULL. Оба **@older_than** и **@larger_than** можно указать.  
  
 [  **@larger_than =**] **"***size_in_bytes***"**  
 Размер в байтах самого большого сохраняемого журнала шагов задания. Удаляются все журналы шагов задания, размер которых превышает указанный. Оба **@larger_than** и **@older_than** можно указать.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_jobsteplog** в **msdb** базы данных.  
  
 Если никакие аргументы, кроме **@job_id** или **@job_name** заданы, удаляются все журналы шагов задания для указанного задания.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** можно удалить журнал шага задания, владельцем которого является другой пользователь.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-removing-all-job-step-logs-from-a-job"></a>A. Удаление всех журналов шагов определенного задания  
 В следующем примере удаляются все журналы шагов задания `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup';  
GO  
```  
  
### <a name="b-removing-the-job-step-log-for-a-particular-job-step"></a>Б. Удаление журнала определенного шага задания  
 В следующем примере удаляется журнал для шага 2 задания `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 2;  
GO  
```  
  
### <a name="c-removing-all-job-step-logs-based-on-age-and-size"></a>В. Удаление всех журналов шагов задания по дате создания и размеру  
 В следующем примере удаляются все журналы шагов задания `Weekly Sales Data Backup`, созданные до полудня 25 октября 2005 года, размер которых превышает 100 МБ.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @older_than = '10/25/2005 12:00:00',  
    @larger_than = 104857600;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
