---
title: sp_help_jobsteplog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5f8ce4b84dc7fd8e049cc9fafd71995dfb09bca7
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392878"
---
# <a name="sphelpjobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает метаданные об определенном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнала шага задания агента. **sp_help_jobsteplog** не возвращает сам журнал.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@job_id =**] **'***job_id***'**  
 Идентификационный номер задачи, для которого возвращаются сведения из журнала шагов задания. *job_id* — **int**, значение по умолчанию NULL.  
  
 [  **@job_name =**] **"***имя_задания***"**  
 Имя задания. *имя_задания* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *имя_задания* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@step_id =**] *step_id*  
 Идентификатор этапа задания. Если не указан, включаются все этапы задания. *step_id* — **int**, значение по умолчанию NULL.  
  
 [  **@step_name =**] **"***step_name***"**  
 Имя шага задания. *step_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания.|  
|**job_name**|**sysname**|Имя задания.|  
|**step_id**|**int**|Идентификатор для этапа задачи. Например, если этот шаг является первым шагом в задание его *step_id* -1.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**step_uid**|**uniqueidentifier**|Уникальный идентификатор этапа (задается системой) задачи.|  
|**date_created**|**datetime**|Дата создания этапа.|  
|**date_modified**|**datetime**|Дата последнего изменения этапа.|  
|**log_size**|**float**|Размер журнала шага задания в мегабайтах (МБ).|  
|**журнал**|**nvarchar(max)**|Вывод журнала шага задания.|  
  
## <a name="remarks"></a>Примечания  
 **sp_help_jobsteplog** в **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Членами **SQLAgentUserRole** могут только просматривать метаданные из журнала шага задания для шагов задания, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. Возвращает сведения из журнала шагов задания для всех шагов в указанной задаче  
 В следующем примере выполняется возврат сведений из журнала шагов задания с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>Б. Возвращает сведения из журнала шага задания для определенного шага  
 В следующем примере выполняется возврат сведений журнала шагов задания для первого этапа задачи с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
