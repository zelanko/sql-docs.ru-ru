---
title: sp_help_jobsteplog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
author: stevestein
ms.author: sstein
ms.openlocfilehash: e3af6ff05b971e6b9a0dedc1ec2e14f4ba87e00c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090042"
---
# <a name="sp_help_jobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает метаданные о конкретном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнале шагов задания агента. **sp_help_jobsteplog** не возвращает фактический журнал.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] 'job_id'`Идентификационный номер задания, для которого возвращаются сведения журнала шагов задания. *job_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @step_id = ] step_id`Идентификационный номер этапа в задании. Если не указан, включаются все этапы задания. *step_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @step_name = ] 'step_name'`Имя шага в задании. Аргумент *step_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**UNIQUEIDENTIFIER**|Уникальный идентификатор задания.|  
|**job_name**|**имеет sysname**|Имя задания.|  
|**step_id**|**int**|Идентификатор для этапа задачи. Например, если шаг является первым шагом в задании, его *step_id* имеет значение 1.|  
|**step_name**|**имеет sysname**|Имя шага задания.|  
|**step_uid**|**UNIQUEIDENTIFIER**|Уникальный идентификатор этапа (задается системой) задачи.|  
|**date_created**|**datetime**|Дата создания этапа.|  
|**date_modified**|**datetime**|Дата последнего изменения этапа.|  
|**log_size**|**float**|Размер журнала шага задания в мегабайтах (МБ).|  
|**Журналь**|**nvarchar(max)**|Вывод журнала шага задания.|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_jobsteplog** находится в базе данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эта хранимая процедура может выполняться членами предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены **SQLAgentUserRole** могут просматривать метаданные журнала шага задания только для тех шагов заданий, которыми они владеют.  
  
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
  
## <a name="see-also"></a>См. также:  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
