---
title: sp_help_jobsteplog (Transact-SQL) | Документы Microsoft
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
ms.openlocfilehash: d439a2fb01d2b6590a6bba226f98cf0a011657eb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 Идентификационный номер задачи, для которого возвращаются сведения из журнала шагов задания. *Аргумент job_id* — **int**, значение по умолчанию NULL.  
  
 [  **@job_name =**] **"***job_name***"**  
 Имя задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
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
|**step_id**|**int**|Идентификатор для этапа задачи. Например, если этап является первым шагом в задании его *step_id* -1.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**step_uid**|**uniqueidentifier**|Уникальный идентификатор этапа (задается системой) задачи.|  
|**date_created**|**datetime**|Дата создания этапа.|  
|**date_modified**|**datetime**|Дата последнего изменения этапа.|  
|**log_size**|**float**|Размер журнала шага задания в мегабайтах (МБ).|  
|**журнал**|**nvarchar(max)**|Вывод журнала шага задания.|  
  
## <a name="remarks"></a>Замечания  
 **sp_help_jobsteplog** в **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** могут только просматривать метаданные из журнала шага задания для шагов задания, которыми они владеют.  
  
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
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
